<template>
  <main class="flex flex-col align-center justify-center text-center" v-if="!loading">
    <div>
      <LinkBoxes />
    </div>
    <div class="border-2 p-5 m-10 shadow-lg rounded-xl">
    <DataTitle :text='title' :dataDate='dataDate' />
    <DataBoxes :stats='stats' />
    </div>
    <div class="border-2 p-5 m-10 shadow-md rounded-xl">
    <CountrySelect @get-country='getLocalData' :countries='countries'/>
    <LocalBox  :localTitle='localTitle' :localStats='localStats'/>
    </div>
  </main>
 <main class="flex flex-col align-center justify-center text-center" v-else>
   <div class="text-gray-500 text-3l">Fetching data..</div>
   <img :src="loadingImage" class="mx-auto" width="125" alt="">
 </main>
</template>
<script>
import DataTitle from '@/components/DataTitle.vue';
import DataBoxes from '@/components/DataBoxes.vue';
import CountrySelect from '@/components/CountrySelect.vue';
import LocalBox from '@/components/LocalBox.vue';
import LinkBoxes from '@/components/LinkBoxes.vue';

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
    LocalBox,
    LinkBoxes
  },
  data() {
    return {
      localTitle: '' || 'Choose country',
      localStats: {},
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: 'https://icon-library.com/images/loading-icon-animated-gif/loading-icon-animated-gif-6.jpg',
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      return data;
    },
    getLocalData(country) {
      this.localTitle = country.Country;
      this.localStats = country;
      console.log(this.localStats);
    }
  },
  async created() {
    const data = await this.fetchCovidData();
    console.log(data);
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },

};
</script>
