<template>
  <div class="box">
    <video id="video" :src="movies[indexNumber].film" controls></video>
  </div>
</template>

<script>


export default {
  name: "videoscreen",
  props: {
    movies: {
      type: Array,
      require: true
    },
    indexNumber: {
      type: Number,
      require: true,
    }
  },
  methods: {}

}
</script>

<style scoped>
video {
  width: 90%;
  height: 67.7vh;
  background-color: papayawhip;
  outline: none;
  background-image: url("~@/assets/curtains.png");

}
.box {
  width: 100%;
  height: 100%;

}
</style>