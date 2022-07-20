<template>
  <main>
    <div class="container py-5">
        <div class="row d-flex flex-wrap gap-4 justify-content-center">

            <albumCard v-for="(album, index) in musicAlbum" :key="index"
            :imgUrl="album.poster"
            :title="album.title"
            :author="album.author"
            :year="album.year"
            />

        </div>
    </div>

  </main>
</template>

<script>
import axios from 'axios';
import albumCard from './albumCard.vue';

export default {
    name: "Main",
    components:{
        albumCard,
    },

    data: function(){
        return{
            musicAlbum: [],
        }
    },

    methods:{
        getMusicAlbums(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {
                this.musicAlbum = result.data.response;
                console.log(this.musicAlbum);
            })
            .catch((error) => {
                console.warn(error);
            })
        }
    },

    created(){
        this.getMusicAlbums();
    }
}
</script>

<style lang="scss" scoped>
    main{
        background-color: #1e2d3b;

        .container{
            max-width: 1000px;
        }
    }
</style>