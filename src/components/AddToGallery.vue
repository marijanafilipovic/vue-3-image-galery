<script setup>
import { ref } from "vue";
const props = defineProps({
  addToGallery : {
    type: Function,
    require: true
  }
})
const imageUrl = ref("");
const imageTitle = ref("");
const handleSubmit = () => {
  const slide = {
    id : new Date().getTime(),
    url : imageUrl.value,
    title : imageTitle.value
  }
  props.addToGallery(slide);
  imageUrl.value = '';
  imageTitle.value = '';
}
</script>
<template>
  <form @submit.prevent="handleSubmit">
    <div>
      <label for="imageUrl">Image Link</label>
      <input id="imageUrl" type="text" v-model="imageUrl"/>
    </div>
    <div>
      <label for="imageTitle">Image Title</label>
      <input id="imageTitle" type="text" v-model="imageTitle"/>
    </div>
    <div>
      <button type="submit" name="addToGallery">Add to gallery</button>
    </div>
  </form>
</template>
<style>

</style>
