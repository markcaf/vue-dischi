<template>
  <div class="col-4 mb-4 text-center">
    <select class="form-select" aria-label="Select by genre" v-model="selectedElement">
        <option selected>Filtra in base al genere</option>
        <option class="text-uppercase" v-for="(content, index) in contents" :key="index" :value="index">
          {{ content }}
        </option>
    </select>

    <button class="btn btn-primary text-white mt-2" @click="$emit('filter', contents[selectedElement]), selectedElement = ''">
        <a class="text-white" href="#">Filtra</a>
    </button>

    <button class="btn btn-primary text-white mt-2 ms-2" @click="$emit('filter', contents[selectedElement]), selectedElement = ''">
        <a class="text-white" href="#">Reset</a>
    </button>
  </div>
</template>

<script>
export default {
    name: "selectGenre",

    props: {
        data: String,
        contents: Array,
    },

    data: function() {
        return {
            selectedElement: "",
        }
    },
}
</script>

<style lang="scss" scoped>

    button{
        a{
            text-decoration: none;
        }
    }

</style>