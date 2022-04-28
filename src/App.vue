<template>
  <the-header></the-header>
  <the-filters @fetch-movies="handleFilters" ></the-filters>
  <LoadingSpinner v-if="loading" />
  <movies-list v-else :movies="moviesData" ></movies-list>
</template>

<script>


import TheHeader from './components/layout/TheHeader.vue'
import TheFilters from './components/layout/TheFilters.vue'
import MoviesList from './components/MoviesList.vue';
import LoadingSpinner from './components/layout/LoadingSpinner.vue';
import { API_KEY } from './config/constants';

export default {
  name: 'App',
  components: {
    TheHeader,
    TheFilters,
    MoviesList,
    LoadingSpinner
},
  data() {
    return {
      moviesData: [],
      errors: null,
      loading: false,
      offsetNum: 0,
      movieOrder: "by-opening-date",
      query: ""
    }
  },
  methods: {
    handleFilters(movieOrder, search) {
      this.movieOrder = movieOrder;
      this.query = search;
      // this.fetchMovies(this.offsetNum, movieOrder, search);
      this.fetchMovies(this.offsetNum, this.movieOrder, this.query);
    },
    async fetchMovies(offsetNum = 0, movieOrder = "by-opening-date", query = "") {
        this.error = null;
        this.loading = true;
        try {
            const response = await fetch(`https://api.nytimes.com/svc/movies/v2/reviews/picks.json?api-key=${API_KEY}&offset=${offsetNum}&order=${movieOrder}&query=${query}`);
            if (!response.ok) {
                const error = new Error("Failed to fetch Data");
                error.statusCode = 404;
                throw error;
            }
            else {
                const data = await response.json();
                this.moviesData = data.results;
                this.loading = false;
                console.log(data.results);
            }
        } catch (error) {
            console.log(error);
            this.error = "Something went wrong - try again later!";
        }
    }
  },
  async mounted() {
       await this.fetchMovies();
  }
}
</script>


