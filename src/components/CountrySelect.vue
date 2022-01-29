<template>
 <h2 class="text-3xl">Countries</h2>
    <div class="m-5">
        <select 
            @change="onChange()"
            v-model="selected" 
            class="form-select w-100 text-center mx-auto shadow-xl mx-10 p-5 rounded">
            <option value="0">Select Country</option>
            <option v-for="country in countries" :key="country.ID" :value="country.ID">
                {{country.Country}}
            </option>
        </select>
    </div>
</template>
<script>
export default {
    name: 'CountrySelect',
    props: ['countries'],
    data() {
        return {
            selected: 0,
        }
    },
    methods: {
        onChange() {
            
            const country = this.countries.find((item) => item.ID === this.selected)
            this.$emit('get-country', country)
          //   console.log(country.Country)
        } 
    }
}
</script>