<template>
    <select @change="onChange()" v-model="selected">
        <option value="">Select Country</option>
        <option v-for="country in countries"  :value="country.CountryCode" :key="country.CountryCode">{{ country.Country }}</option>
    </select>
</template>

<script>
export default{
    name: 'CountryData',
    props: ['countries'],
    data(){
        return{
            selected : ''
        }
    },
    methods: {
        onChange(){
            const country = this.countries.find((item) => item.CountryCode === this.selected);
            this.$emit('get-country', country);
        }
    }
}
</script>
