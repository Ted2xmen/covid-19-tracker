<template>
    <div class="grid md:grid-cols-1 gap-4 p-4 m-4">
        <!-- box 1 -->
        <div class="shadow-xl text-center rounded p-7 bg-blue-600">
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
    </div>
</template>
<script>
export default {
    name: 'LocalBox',
    props: ['localTitle', 'localStats'],
}
</script>