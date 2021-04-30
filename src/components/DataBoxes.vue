<template>
    <div class="data-boxes">
        <div>
            <h2>Confirmed</h2>
            <p>NewConfirmed: {{ numberWithComma(stats.NewConfirmed) }}</p>
            <p>TotalConfirmed: {{ numberWithComma(stats.TotalConfirmed) }}</p>
        </div>

        <div>
            <h2>Deaths</h2>
            <p>NewDeaths: {{ numberWithComma(stats.NewDeaths) }}</p>
            <p>TotalDeaths: {{ numberWithComma(stats.TotalDeaths) }}</p>
        </div>

        <div>
            <h2>Recovered</h2>
            <p>NewRecovered: {{ numberWithComma(stats.NewRecovered) }}</p>
            <p>TotalRecovered: {{ numberWithComma(stats.TotalRecovered) }}</p>
        </div>
    </div>
</template>

<script>
export default{
    name: 'DataBoxes',
    props: ['stats'],
    methods:{
        numberWithComma(number){
        return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }
    },
}
</script>
