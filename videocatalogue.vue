<template>
  <div class="container">
    <div @click="getIndex(index)" class="movieThumbs" v-for="(movie, index) in filteredMovies" :key="index">
      <img :src="movie.thumb" alt="movie thumbnail">
      <div class="movieTekst">
        <h4>{{ movie.title }}</h4>
        <p class="tekst">{{ movie.desc }}</p>
        <p class="info">{{ movie.actor }}</p>
        <p class="info">{{ movie.year }}</p>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: "videocatalogue",
  data() {
    return {
      clickedIndex: null,

    }
  },
  props: {
    movies: {
      type: Array,
      required: true,
    },
    searchTerm: {
      type: String,
    }
  },
  computed: {
    filteredMovies: function () {
      return this.movies.filter((movie) => {
        return movie.title.toLowerCase().match(this.searchTerm.toLowerCase())
            || movie.desc.toLowerCase().match(this.searchTerm.toLowerCase())
            || movie.actor.toLowerCase().match(this.searchTerm.toLowerCase())
            || movie.year.toLowerCase().match(this.searchTerm.toLowerCase())


      })
    },

  },
  methods: {
    getIndex: function (index) {
      this.clickedIndex = index;
      this.$emit('getIndex', index);
    },
  },
}
</script>

<style scoped>
.container {
  width: 100%;
  max-height: 67.7vh;
  overflow-y: scroll;
  background-color: papayawhip;
  padding: 15px;
  border: 6px solid #760000;

}

.container::-webkit-scrollbar {
  display: none;
}

.movieThumbs {
  height: 35%;
  display: flex;
  margin-bottom: 10px;

}

.movieThumbs:hover {
  cursor: pointer;
}

img {
  width: 30%;
  object-fit: cover;
  height: auto;
  margin-right: 10px;
  object-position: top;
  border-radius: 8px;
  margin-left: 15px;

}

h4 {
  margin: 0;
  padding: 0;
}

.tekst {
  font-family: Avenir, sans-serif;
  font-size: clamp(0.2rem, 1.1vw, 1.2rem);
  max-width: 200px;
}

.movieTekst {
  height: 60%;
}

.info {
  font-size: clamp(0.2rem, 1.1vw, 1.1rem);
}
</style>