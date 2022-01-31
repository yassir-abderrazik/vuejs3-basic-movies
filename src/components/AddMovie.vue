<template lang="">
  <label class="text-gray-600 text-sm font-bold mb-2" for="title">
    Movie Name :
  </label>
  <input
    class="shadow appearance-none border rounded w-full py-2 px-3 bg-gray-800 text-gray-300 leading-tight focus:outline-none focus:shadow-outline"
    id="title"
    type="text"
    placeholder="title"
    v-model="title"
  />
  <div>
    <label class="text-gray-600 text-sm font-bold mb-2" for="image">
      Movie image (url) :
    </label>
    <input
      class="shadow appearance-none border rounded w-full py-2 px-3 bg-gray-800 text-gray-300 leading-tight focus:outline-none focus:shadow-outline"
      id="image"
      type="text"
      placeholder="image"
      v-model="image"
    />
  </div>
  
  <div class="flex flex-col justify-center items-center">
    <button
      class="bg-gray-800 rounded-xl text-white px-4 py-2 my-2"
      @click="newMovie"
    >
      Add Movie
    </button>
  </div>


</template>
<script>
export default {
  data() {
    return {
      title: "",
      image: "",
      category: "",
    
    };
  },
  methods: {
    newMovie() {
      let title = this.title;
      let image = this.image;
      if (title == null || image == null) {
        return;
      } else {
        const movie = {
          title,
          image,
        };
        this.$emit("addMovie", movie);
      }
    },
  },
};
</script>
<style lang=""></style>
