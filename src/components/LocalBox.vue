<template>
    <div class="grid md:grid-cols-2 gap-4 p-4 m-4">
        <!-- box 1 -->
        <div class="shadow-xl text-center justify-items-center bg-blue-600">
            <h3 class="font-bold text-3xl p-1 m-1">
                {{localTitle}} 
            </h3>
            <img :src="`https://countryflagsapi.com/png/${localStats.CountryCode}`" width="150" :alt="localStats.CountryCode">
            <h2>Country Code : {{localStats.CountryCode}} </h2>
            <span class="font-bold">New: </span>
            {{localStats.TotalConfirmed}}
            <br>
            <span class="font-bold">Total: </span>
            {{localStats.TotalDeaths}}
        </div>
        <!-- box 2 -->
        <div class="shadow-xl text-center  bg-blue-600">
            
            <h2>Country Code : {{localStats.CountryCode}} </h2>
            <span class="font-bold">New: </span>
            {{localStats.TotalConfirmed}}
            <br>
            <span class="font-bold">Total: </span>
            {{localStats.TotalDeaths}}
            country info: {{countryInfo}}
            
        </div>
    </div>
</template>
<script>
export default {
    name: 'LocalBox',
    props: ['localTitle', 'localStats'],
    data() {
        return {
            countryInfo: [],
         
        }
    },
    methods: {
        
    async fetchCountryData(code) {
     const res = await fetch('https://restcountries.com/v3.1/all');
     const data = await res.json(); 
     let filtered = data.filter(item => item.cca2 === code);
     this.countryInfo.push(filtered);
     console.log(filtered);
     
    },
    },
    
     created() {
     this.fetchCountryData(this.localStats.CountryCode);
    }
}
</script>