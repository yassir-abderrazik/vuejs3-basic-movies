<template lang="">
  <div>
    <img
      alt="person capturing an image"
      :src="movie.image"
      class="h-64 w-full rounded-2xl"
    />
  </div>
  <div class="p-2">
    <h2 class="text-lg font-semibold text-gray-300 text-center">
      {{ movie.title }}
    </h2>
    <p class="text-gray-400">
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Eius fugiat
      ratione neque ...
    </p>
    <div class="flex justify-center">
        <button class="bg-red-500 text-white py-2 px-4 m-2 rounded-lg" @click='deleteMovie(movie.id)'>DELETE</button>
    </div>
  </div>
</template>
<script>
export default {
    props: ['movie'],
    methods: {
        deleteMovie(id) {
            this.$emit('delete', id)
        }
    },
};
</script>
<style lang=""></style>
