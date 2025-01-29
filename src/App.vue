<script setup>
import { ref } from "vue";
import Carousel from "./components/Carousel.vue";

const images = ref([
  {
    id: "asd234",
    url: "https://gratisography.com/wp-content/uploads/2024/11/gratisography-augmented-reality-800x525.jpg",
    title: "img-title1",
  },
  {
    id: "sdf543",
    url: "https://www.w3schools.com/css/img_5terre.jpg",
    title: "img-title2",
  },
  {
    id: "tre456",
    url: "https://gratisography.com/wp-content/uploads/2024/10/gratisography-cool-cat-800x525.jpg",
    title: "img-title3",
  },
]);
const removeImg = (i) => {
  images.value = images.value.filter((image, index) => index !== i);
};
</script>

<template>
  <header></header>

  <main>
    <div v-if="images.length > 0" class="images">
      <div v-for="(image, index) in images" :key="image.id" class="image">
        <h1>{{ index + 1 }}: {{ image.title }}</h1>
        <img :src="image.url" :alt="image.title" />
        <button @click="removeImg(index)" class="remove">Remove</button>
      </div>
    </div>
    <div v-else class="no-images"><h2>No Images</h2></div>
    <hr />
    <Carousel />
  </main>
</template>

<style scoped>
.images {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 20px;
  padding: 20px;
}
.image {
  display: flex;
  flex-direction: column;
  align-items: start;
  width: 20rem;
  border: solid 1px black;
  margin: 10px;
  padding: 15px;
  border-radius: 10px;
  background: rgba(246, 238, 221, 0.84);
}
img {
  width: 100%;
}
.remove {
  margin-top: 10px;
  padding: 10px 15px;
  background-color: rgb(250, 110, 110);
  color: black;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
}
.remove:hover {
  background: rgb(182, 7, 42);
  color: white;
}
.no-images {
  text-align: center;
  font-size: 1.5rem;
  margin: 20px 0;
}
</style>
