<template lang="">
  <div class="w-2/5" v-bind:class="[isOpen ? ' ' : 'hidden']" id="addMovie">
    <AddMovie @addMovie="addNewMovie($event)" />
  </div>
  <slot></slot>
  <button
    class="bg-gray-800 rounded-xl text-white px-4 py-2 my-2"
    @click="hiddenAddMovie"
  >
    {{ isOpen ? "close" : "Add New Movie" }}
  </button>
  <div class="flex">
    <label class="text-gray-600 text-sm font-bold mb-2" for="image">
      Search
    </label>
    <input
      type="text"
      class="shadow appearance-none border rounded w-full mb-2 bg-gray-800 text-gray-300 leading-tight focus:outline-none focus:shadow-outline"
      v-model="search"
    />
  </div>
  <div class="grid lg:grid-cols-4 md:grid-cols-1 gap-4">
    <div
      class="rounded-2xl mx-8 border-2 border-sky-300"
      v-for="movie in filteredList"
      :key="movie.id"
    >
      <Movie :movie="movie" @delete="deleteOneMovie($event)" />
    </div>
  </div>
  <teleport to="#alert" v-if="movieDeleted">
    <div
      class="flex bg-red-100 rounded-lg fixed mt-20 mr-10 right-0 top-0 py-4 px-4 text-sm text-red-700"
      role="alert"
    >
      <svg
        class="w-5 h-5 inline mr-3"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          fill-rule="evenodd"
          d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z"
          clip-rule="evenodd"
        ></path>
      </svg>
      <div><span class="font-medium">Deleted !</span> Movie</div>
    </div>
  </teleport>
</template>
<script>
import Movie from "./Movie.vue";
import AddMovie from "./AddMovie.vue";

export default {
  components: {
    Movie,
    AddMovie,
  },
  data() {
    return {
      search: "",
      movieDeleted: false,
      isOpen: false,
      movies: [
        {
          id: 1,
          title: "Spider-Man: No Way Home",
          image:
            "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTrdPsGJEBxBev7gKo_EMp0Pgk7Q7su_xTUxf3vo8dE9S_CiG2Z",
        },
        {
          id: 2,
          title: "Kimetsu no Yaiba the Movie: Mugen Train",
          image:
            "https://upload.wikimedia.org/wikipedia/en/2/21/Kimetsu_no_Yaiba_Mugen_Ressha_Hen_Poster.jpg",
        },
        {
          id: 3,
          title: "Joker",
          image:
            "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQuTcvL4wc0fbBjm1h5CRiFEZ2TnNKtu8KtoPSxTsj6mkedHeWl",
        },
        {
          id: 4,
          title: "Interstellar",
          image:
            "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRf61mker2o4KH3CbVE7Zw5B1-VogMH8LfZHEaq3UdCMLxARZAB",
        },
      ],
    };
  },
  methods: {
    deleteOneMovie(id) {
      this.movies = this.movies.filter((movie) => movie.id != id);
      this.movieDeleted = true;
      setTimeout(() => {
        this.movieDeleted = false;
      }, 3000);
    },
    addNewMovie(movie) {
      this.movies.unshift(movie);
    },
    hiddenAddMovie() {
      this.isOpen = !this.isOpen;
    },
  },
  computed: {
    filteredList() {
      return this.movies.filter((movie) => {
        return movie.title.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
};
</script>
<style lang=""></style>
