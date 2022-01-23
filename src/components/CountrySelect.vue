<template>
    <div>
        <select 
            @change="onChange()"
            v-model="selected" 
            class="form-select  w-100 mx-10 p-5 rounded">

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
    emits: ['get-country'],
    data() {
        return {
            selected: 0,
        }
    },
    methods: {
        onChange() {
            const country = this.countries.find((item) => item.ID === this.selected)
            this.$emit('get-country', country)
             console.log('click')
        } 
    }
    
}
</script>