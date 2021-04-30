<template>
    <div class="data-title">
        <h2>{{ text }}</h2>
        <p>{{ dataDate }}</p>
    </div>
</template>

<script>
export default{
    name: 'DataTitle',
    props: ['text', 'dataDate']
}
</script>
