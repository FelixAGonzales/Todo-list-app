<script>
export default {
  props: {
    photos: Array,
  },
};
</script>

<template>
  <div>
    <h1>To do List</h1>
    <div v-for="photo in photos" v-bind:key="photo.id">
      <h2>{{ photo.name }}</h2>
      <img v-bind:src="photo.url" />
      <p>Width: {{ photo.width }}</p>
      <p>Height: {{ photo.height }}</p>
    </div>
  </div>
</template>

<style></style>