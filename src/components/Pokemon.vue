<template>
    <div>     


        <div class="card">
            <div class="card-image">
                <figure class="image is-4by3">
                <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
                </figure>
            </div>
            <div class="card-content">
                <div class="media">
                <div class="media-content">
                    <p class="title is-4">{{ num + " " + formattedName }}</p>
                    <p class="subtitle is-6">{{ pokemon.type }}</p>
                </div>
                </div>

                <div class="content">

                </div>
            </div>
        </div>




    </div>

</template>

<script>
import axios from 'axios';

export default {
    created: function(){
        axios.get(this.url).then(res => {
            console.log(res.data)
            this.pokemon.type = res.data.types[0].type.name;
            this.pokemon.front = res.data.sprites.front_default;
            this.pokemon.back = res.data.sprites.back_default;
        })
    },
    data(){
        return {
            pokemon: {}
        }
    },   
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