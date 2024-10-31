<script>
import PhotosIndex from "./PhotosIndex.vue";
import PhotosNew from "./PhotosNew.vue";
import PhotosShow from "./PhotosShow.vue";
import Modal from "./Modal.vue";
import axios from "axios";

axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';

export default {
  components: {
    PhotosIndex,
    PhotosNew,
    PhotosShow,
    Modal,
  },


  data: function () {
    return {
      photos: [],
      currentPhoto: {},
      isPhotosShowVisible: false,
    };
  },


  // data: function () {
  //   return {
  //     photos: [
  //     { id: 1, catergory: "Personal", date: "2024-01-11", title: "Grocery Shopping", description: "Buy groceries for the week", status:"Pending" },
  //     { id: 2, catergory: "Exercise", date: "2024-29-10", title: "Working Out", description: "Go to the gym", status:"Completed" },
  //     { id: 3, catergory: "Academic", date: "2024-30-10", title: "Exam Review", description: "Study for Chemistry Exam", status:"Pending" },
  //     { id: 4, catergory: "Work", date: "2024-03-11", title: "Finish Report", description: "Complete monthly report", status:"Pending" },
  //     ],
  //   }
  // },


  created: function () {
    this.handleIndexPhotos();
  },
  methods: {
    handleIndexPhotos: function () {
      axios.get("http://localhost:5000/tasks.json").then((response) => {
        console.log("photos index", response);
        this.photos = response.data;
      });
    },
    handleCreatePhoto: function (params) {
      axios
        .post("http://localhost:5000/tasks.json", params)
        .then((response) => {
          console.log("photos create", response);
          this.photos.push(response.data);
        })
        .catch((error) => {
          console.log("photos create error", error.response);
        })
    },
    handleShowPhoto: function (photo) {
      console.log("handleShowPhoto", photo);
      this.currentPhoto = photo;
      this.isPhotosShowVisible = true;
    },

    handleUpdatePhoto: function (id, params) {
      console.log("handleUpdatePhoto", id, params);
      axios
        .patch(`http://localhost:5000/tasks/${id}.json`, params)
        .then((response) => {
          console.log("photos update", response);
          this.photos = this.photos.map((photo) => {
            if (photo.id === response.data.id) {
              return response.data;
            } else {
              return photo;
            }
          });
          this.handleClose();
        })
        .catch((error) => {
          console.log("photos update error", error.response);
        });
    },

    handleClose: function () {
      this.isPhotosShowVisible = false;
    },
  },

};
</script>



<template>
  <main>
    <PhotosNew v-on:createPhoto="handleCreatePhoto"/>
    <PhotosIndex v-bind:photos="photos" v-on:showPhoto="handleShowPhoto"/>
    <Modal v-bind:show="isPhotosShowVisible" v-on:close="handleClose">
      <PhotosShow v-bind:photo="currentPhoto" v-on:updatePhoto="handleUpdatePhoto" />
    </Modal>
  </main>
</template>

<style></style>

