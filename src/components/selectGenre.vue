<template>
  <div class="col-4 mb-4 text-center">
    <select class="form-select" aria-label="Select by genre" v-model="selectedElement" @click="$emit('filter', contents[selectedElement])">
        <option selected value="">Mostra tutti i generi</option>
        <option v-for="(content, index) in contents" :key="index" :value="index">
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