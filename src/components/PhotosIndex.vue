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
      <h2>{{ photo.category }}</h2>
      <p>Title: {{ photo.title }}</p>
      <p>Date: {{ photo.date }}</p>
      <p>Description: {{ photo.description }}</p>
      <p>Status: {{ photo.status }}</p>
      <button v-on:click="$emit('showPhoto', photo)">More Info</button>
    </div>
  </div>
</template>

<style></style>