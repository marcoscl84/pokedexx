<template>
    <div>
        <h1>{{ num + " " + formattedName }}</h1>
        <small>{{ url }}</small>
        hr
    </div>

</template>

<script>
export default {
    name: 'PokemonComponent',
    props: {
        num: Number,
        name: String,
        url: String
    },
    computed: {
        formattedName() {
            return this.name ? this.name.charAt(0).toUpperCase() + this.name.slice(1) : '';
        }
    }
}
</script>

<style>

</style>