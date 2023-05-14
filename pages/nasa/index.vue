<template>
    <div style="text-align: center;">
      <h1>You are searching for: {{ message }}</h1>
      <input v-model="message" placeholder="search">
      <button @click="find()">Szukaj</button>
      <div style="display:flex; flex-wrap: wrap; width: 100vw; justify-content: center;">
        <img
          v-if="hasImage(value)"
          :src="getImageSrc(value)"
          v-for="(value, index) in dataArray"
          :key="index"
          style="width: 100px; height: 100px; object-fit: cover; padding: 5px;"
          @click="openGallery(index)"
        />
      </div>
      <div v-show="isGalleryOpen" class="gallery-overlay">
        <button class="close-button" @click="closeGallery()">Close</button>
        <div class="gallery-content">
          <img
            v-if="hasActiveImage()"
            :src="getActiveImageSrc()"
            alt="Gallery Image"
          />
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  export default {
    name: "index",
  
    created() {
      this.fetchData("sun");
      this.message = "";
    },
  
    data() {
      return {
        dataArray: [],
        message: "",
        isGalleryOpen: false,
        activeIndex: 0,
      };
    },
  
    methods: {
      find() {
        this.fetchData(this.message);
        this.message = "";
      },
      async fetchData(search) {
        try {
          const response = await axios.get(
            "https://images-api.nasa.gov/search?q=" + search
          );
          this.dataArray = response.data.collection.items;
        } catch (error) {
          console.log(error);
        }
      },
      hasImage(value) {
        return value && value.links && value.links.length > 0;
      },
      getImageSrc(value) {
        if (this.hasImage(value)) {
          return value.links[0].href;
        }
        return "";
      },
      openGallery(index) {
        this.activeIndex = index;
        this.isGalleryOpen = true;
      },
      closeGallery() {
        this.isGalleryOpen = false;
      },
      hasActiveImage() {
        const activeValue = this.dataArray[this.activeIndex];
        return this.hasImage(activeValue);
      },
      getActiveImageSrc() {
        const activeValue = this.dataArray[this.activeIndex];
        if (this.hasImage(activeValue)) {
          return activeValue.links[0].href;
        }
        return "";
      },
    },
  };
  </script>
  
  <style scoped>
  .gallery-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.9);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
  }
  
  .close-button {
    position: absolute;
    top: 10px;
    right: 10px;
  }
  
  .gallery-content img {
    max-width: 90%;
    max-height: 90%;
  }
  </style>
  