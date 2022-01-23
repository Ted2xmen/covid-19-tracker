<template>
    <div class="grid md:grid-cols-2 gap-4 p-2 m-2">
        <!-- box 1 -->
        <div class="shadow-xl text-center rounded p-7  bg-indigo-400 hover:bg-indigo-700">
            <h3 class="font-bold text-3xl p-1 m-1">Cases</h3>
            <span class="font-bold">New: </span>
            {{numberWithCommas(stats.NewConfirmed)}}
            <br>
            <span class="font-bold">Total: </span>
            {{numberWithCommas(stats.TotalConfirmed)}}
        </div>
        <!-- box 2  -->
    <div class="shadow-xl text-center rounded p-7 bg-indigo-200 hover:bg-purple-500">
            <h3 class="font-bold text-3xl p-1 m-1">Deaths</h3>
            <span class="font-bold">New: </span>
            {{numberWithCommas(stats.NewDeaths)}}
            <br>
            <span class="font-bold">Total: </span>
            {{numberWithCommas(stats.TotalDeaths)}}
        </div>
    </div>
</template>
<script>
export default {
    name: 'DataBoxes',
    props: ['stats'],
    methods: {
        numberWithCommas(x) {
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
}
</script>