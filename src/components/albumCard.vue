<template>
  <div class="col-2 album-card text-center">
    <div class="image-container">
        <img :src="imgUrl" alt="title">
    </div>

    <div class="title">
        {{ title }}
    </div>
    
    <div class="author">
        {{ author }}
    </div>

    <div class="year">
        {{ year }}
    </div>
</div>
</template>

<script>
export default {
  props: {
    imgUrl: String,
    title: String,
    author: String,
    year: String,
  },
};
</script>

<style lang="scss" scoped>
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
</style>