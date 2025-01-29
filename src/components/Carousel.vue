<script setup>
import { ref } from "vue";
const imag = ref(0);
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
const imgUrl = ref("");

const handleDown = () => {
  if (imag.value > 0) {
    imag.value--;
  } else {
    imag.value = images.value.length - 1;
  }
};

const handleUp = () => {
  if (imag.value < images.value.length - 1) {
    imag.value++;
  } else {
    imag.value = 0;
  }
};
const deliteImage = (inx) => {
  images.value = images.value.filter((image, index) => index !== inx);
};
const addImage = () => {
  const image = {
    id: new Date().getTime(),
    url: imgUrl.value,
    title: `img-title${images.value.length + 1}`,
  };
  images.value.push(image);
  imgUrl.value = "";
};
</script>
<template>
  <div v-if="images.length > 0" class="carousel">
    <div v-for="(image, index) in images" :key="index" class="image">
      <img
        :src="image.url"
        :alt="image.alt"
        class="img"
        :class="imag !== index ? 'show' : ''"
      />
      <hr />
      <p>{{ image.title }}</p>
      <button @click="deliteImage(index)" :class="imag !== index ? 'show' : ''">
        *
      </button>
    </div>
    <button @click="handleDown">-</button>
    <button @click="handleUp">+</button>
    <p>{{ imag }}</p>
  </div>
  <div v-else>
    <p>No images</p>
  </div>
  <form @submit.prevent="addImage">
    <label for="url">Url</label>
    <input id="url" type="text" v-model="imgUrl" required />
    <button>Add</button>
  </form>
</template>
<style>
.img {
  width: 30rem;
}
.show {
  display: none;
}
</style>
