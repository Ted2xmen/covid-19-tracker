<template>
    <div class="grid md:grid-cols-3 gap-0 p-1 mx-5">
        <div class="p-4 mx-3 shadow-md rounded bg-green-400 hover:bg-green-200" 
        v-for="(link, index) in links" :key="index">
            <a :href="link.url" target="_blank">{{link.name}}</a>
        </div>
    </div>
</template>
<script>
export default {
    name: 'LinkBoxes',
    data() {
        return {
            links: [
            {
                'name': 'WHO Coronavirus Dashboard',
                'url': 'https://covid19.who.int/'
            },
            {
                'name': 'JSTOR resources during COVID-19',
                'url': 'https://about.jstor.org/covid19/'
            },
            {
                'name': 'Covid-19 Bilgilendirme Platformu',
                'url': 'https://covid19.saglik.gov.tr/'
            },
                ]
        }
    }
}
</script>