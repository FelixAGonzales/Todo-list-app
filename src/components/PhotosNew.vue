<script>
export default {
  data: function () {
    return {
      newPhotoParams: {},
    };
  },
  methods: {
    handleSubmit: function () {
      this.$emit("createPhoto", this.newPhotoParams);
      this.newPhotoParams = {};
    },
  },
};
</script>

<template>
  <div>
    <h1>New To-Do Item</h1>
    <form v-on:submit.prevent="handleSubmit">
      <div>
        Category:
        <input name="category" type="text" v-model="newPhotoParams.category">
      </div>
      <div>
        Date:
        <input name="date" type="text" v-model="newPhotoParams.date">
      </div>
      <div>
        Title:
        <input name="title" type="text" v-model="newPhotoParams.title">
      </div>
      <div>
        Description:
        <input name="description" type="text" v-model="newPhotoParams.description">
      </div>
      <div>
        Status:
        <input name="status" type="text" v-model="newPhotoParams.status">
      </div>
      <button type="submit">Add To-Do Task</button>
    </form>
  </div>
</template>