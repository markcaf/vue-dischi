<template>
  <div class="col-4 mb-4">
    <select class="form-select" aria-label="Select by genre">
        <option selected>Filtra in base al genere</option>
        <option class="text-uppercase" v-for="(content, index) in contents" :key="index" :value="index">
          {{ content }}
        </option>
    </select>
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
            
        }
    },
}
</script>

<style>

</style>