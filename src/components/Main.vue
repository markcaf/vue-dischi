<template>
  <main>
    <div class="container py-5">
        <div class="row d-flex flex-wrap gap-4 justify-content-center">

            <div class="col-2 album-card text-center" v-for="(album, index) in musicAlbum" :key="index">
                <div class="image-container">
                    <img :src="album.poster" alt="album.title">
                </div>

                <div class="title">
                    {{ album.title }}
                </div>
                
                <div class="author">
                    {{ album.author }}
                </div>

                <div class="year">
                    {{ album.year }}
                </div>
            </div>

        </div>
    </div>

  </main>
</template>

<script>
import axios from 'axios';
export default {
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

            .album-card{
                background-color: #2e3a46;
                height: 320px;

                .image-container{
                    padding: 10px;
                    margin-top: 10px;

                    img{
                        width: 100%;
                    }
                }

                .title{
                    text-transform: uppercase;
                    color: white;
                    font-weight: bold;
                    padding-top: 10px;
                    margin-bottom: 20px;
                    font-size: 20px;
                    line-height: 22px;
                }

                .author,
                .year{
                    color: #6c7675;
                }

            }
        }
    }
</style>