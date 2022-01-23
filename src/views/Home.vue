<template>
  <main class="flex flex-col align-center justify-center text-center" v-if="!loading">
    <DataTitle :text='title' :dataDate='dataDate' />
    <DataBoxes :stats='stats' />
    <LocalBox @get-country='getLocalData' :localTitle='localTitle' />
    <CountrySelect :countries='countries'/>
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


export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
    LocalBox
  },
  data() {
    return {
      localTitle: '',
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
      console.log('sdasd');
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
