<template>
  <div class="w-[90vw] mx-auto mb-32">
    <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 content-start gap-6 ">
        <MovieItem
          v-for="(movie, index) in movies"
          :key="index"
          :title="movie.display_title === null ? 'No Title Found' : movie.display_title "
          :link="movie.link.url"
          :description="movie.summary_short === null ? 'No Summary Found' : movie.summary_short "
          :image="movie.multimedia === null ? 'https://picsum.photos/400/200' : movie.multimedia.src "
          :date="movie.publication_date"
        />
    </div>
  </div>
</template>


<script>
import MovieItem from "./MovieItem.vue";

export default {
  components: { MovieItem },
  props: ["movies"]
};
</script>

