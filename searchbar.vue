<template>
  <div>
    <label>
      <input
          type="text"
          @input="$emit('input',$event.target.value)"
          placeholder="Søk etter tittel, utgivelsesår, skuespiller..."
      >
    </label>
  </div>
</template>

<script>
export default {
  name: "searchbar",
  data() {
    return {
      search: 'something',
    }
  },
  props: {},
}
</script>

<style scoped>
input {
  height: 37px;
  width: 36%;
  font-size: clamp(1.2rem, 11px, 2rem);
  outline: none;
  border: none;
  padding-left: 10px;
  background-color: papayawhip;
  font-family: "Source Sans Pro", Arial, serif;
  color: black;
}

</style>