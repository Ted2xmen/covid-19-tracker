<template>
  <div class="grid md:grid-cols-2 gap-4 p-4 m-4">
    <!-- box 1 -->
    <div class="shadow-xl text-center justify-items-center bg-blue-600 p-7 hover:bg-blue-400">
      <h3 class="font-bold text-4xl p-1 m-1">
        {{ localTitle }}
      </h3>
      <img v-if="localStats.CountryCode"
        :src="`https://countryflagsapi.com/png/${localStats.CountryCode}`"
        width="200"
        :alt="localStats.CountryCode"
        class="mx-auto p-5"
      />
      <h2>Country Code : {{ localStats.CountryCode }}</h2>
      <div class="p-2">
        <span class="font-bold">New Confirmed: </span>
        {{ localStats.TotalConfirmed }}
        <br />
        <span class="font-bold">Total Deaths: </span>
        {{ localStats.TotalDeaths }}
      </div>
    </div>
    <!-- local info box 2 -->
    <TheBox :countryName="countryName" :capital="capital" :population="population"  />

  </div>
</template>
<script>
import TheBox from '@/components/TheBox.vue'

export default {
  name: "LocalBox",
  components: {
    TheBox
  },
  props: ["localTitle", "localStats"],
  data() {
    return {
      faker: '',
      countryInfo: [],
      countryName: "",
      capital: "",
      population: null,
      icon: null,
      lang: {},
    };
  },
  methods: {
    async fetchCountryData(code) {
      const res = await fetch(`https://restcountries.com/v3.1/alpha/${code}`);
      const data = await res.json();
      //old api -  let filtered = data.filter(item => item.cca2 === code);
      this.countryName = data[0].altSpellings[1];
      this.capital = data[0].capital[0];
      this.population = data[0].population;
      this.lang = data[0].languages;
      this.icon = data[0].flag;
      this.countryInfo.push(data);
    },
  },
  created() {
    // not working auto now. manuel..
    this.fetchCountryData("fr");
  },
};
</script>
