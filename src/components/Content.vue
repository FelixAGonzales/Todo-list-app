<script>
import PhotosIndex from "./PhotosIndex.vue";
import axios from "axios";

export default {
  components: {
    PhotosIndex,
  },
  data: function () {
    return {
      photos: [
      { id: 1, catergory: "Personal", date: "2024-01-11", title: "Grocery Shopping", description: "Buy groceries for the week", status:"Pending" },
      { id: 2, catergory: "Exercise", date: "2024-29-10", title: "Working Out", description: "Go to the gym", status:"Completed" },
      { id: 3, catergory: "Academic", date: "2024-30-10", title: "Exam Review", description: "Study for Chemistry Exam", status:"Pending" },
      { id: 4, catergory: "Work", date: "2024-03-11", title: "Finish Report", description: "Complete monthly report", status:"Pending" },
      ],
    }
  }
};
</script>



<template>
  <main>
    <PhotosIndex v-bind:photos="photos" />
  </main>
</template>

<style></style>

category 
date
tiutle
description
status