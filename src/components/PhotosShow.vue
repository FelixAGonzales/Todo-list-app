<script>
export default {
  props: {
    photo: Object,
  },
  data: function () {
    return {
      editPhotoParams: {},
    };
  },
  created: function () {
    this.editPhotoParams = { ...this.photo };
  },
  methods: {
    handleSubmit: function () {
      this.$emit("updatePhoto", this.photo.id, this.editPhotoParams);
    },
  },
};
</script>

<template>
  <div>
    <h1>Task Information</h1>
    <p>{{ photo.category }}</p>
    <p>Title: {{ photo.title }}</p>
    <p>Date: {{ photo.date }}</p>
    <p>Description: {{ photo.description }}</p>
    <p>Status: {{ photo.status }}</p>
    <form v-on:submit.prevent="handleSubmit">
      <div>
        Category:
        <input name="category" type="text" v-model="editPhotoParams.category">
      </div>
      <div>
        Date:
        <input name="date" type="text" v-model="editPhotoParams.date">
      </div>
      <div>
        Title:
        <input name="title" type="text" v-model="editPhotoParams.title">
      </div>
      <div>
        Description:
        <input name="description" type="text" v-model="editPhotoParams.description">
      </div>
      <div>
        Status:
        <input name="status" type="text" v-model="editPhotoParams.status">
      </div>
      <button type="submit">Add To-Do Task</button>
    </form>
  </div>
</template>

<style></style>