<template>
  <main>
    <div class="container py-5">
        <div class="row justify-content-center">
            <selectGenre @filter="getMusicAlbums"
            v-for="(info, index) in albumData" :key="index"
            :data="info.data"
            :contents="info.content"/>
        </div>

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
import selectGenre from './selectGenre.vue';

export default {
    name: "Main",
    components:{
        selectGenre,
        albumCard,
    },

    data: function(){
        return{
            musicAlbum: [],
            genres: [],
            albumData: [],
        }
    },

    methods:{
        getMusicAlbums(elementToFilter){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {
                this.musicAlbum = result.data.response;
                console.log(this.musicAlbum);

                // Recupero i dati sul genere dalla variabile musicAlbum, popolata dalla chiamati API
                for (let i=0; i < this.musicAlbum.length ; i++){
                    // Inserisco i dati in un array denominato genres
                    this.genres.push(result.data.response[i].genre);
                }
                console.log(this.genres);

                // Rimuovo i duplicati dell'array
                this.genres = [... new Set(this.genres)];
                console.log(this.genres);

                // Creato un array di oggetti con i dati dei generi
                this.albumData = [
                    {
                        data: "genres", 
                        content: this.genres,
                    }
                ];
                console.log(this.albumData);

                // Condizione sull'argomento per filtrare i risultati
                // L'argomento passato sarà il valore del v-model 'selectedElement' nel figlio, ovvero l'opzione scelta nella select
                if (elementToFilter == "") {
                        this.musicAlbum = response.data.response;
                    } else {
                        const filteredElement = this.musicAlbum.filter((album) => album.genre.toLowerCase() == elementToFilter.toLowerCase());
                        this.musicAlbum = filteredElement;
                    }
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