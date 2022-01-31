<template>
  <Header />
  <div class="flex flex-col items-center mt-16">
    <img alt="Vue logo" src="./assets/logo.png" />

    <Movies>
      <h1 class="text-4xl my-4 text-gray-400">List of Movies</h1>
      <template v-slot:buttonAdd>
          add New Movie        
      </template>
      <template v-slot:closeButton>
          close        
      </template>
    </Movies>
  </div>
  <Footer url="https://github.com/yassir-abderrazik" />
</template>

<script>
import Header from "./components/Header.vue";
import Movies from "./components/Movies.vue";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Header,
    Movies,
    Footer,
  },
};
</script>
