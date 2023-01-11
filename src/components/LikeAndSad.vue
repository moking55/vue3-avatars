<template>
  <div class="btn-group">
    <button
      type="button"
      @click="incrementLikes"
      class="btn btn-sm btn-outline-success"
    >
      <i class="fas fa-thumbs-up"></i>
      Like {{ likes }}
    </button>
    <button
      type="button"
      @click="incrementDislikes"
      class="btn btn-sm btn-outline-danger"
    >
      <i class="fas fa-sad-tear"></i>
      Sad {{ dislikes }}
    </button>
  </div>
</template>
<script setup>
import { ref } from "vue";
var [likes, dislikes] = [ref(0), ref(0)];
function incrementLikes() {
  return likes.value++;
}
function incrementDislikes() {
  return dislikes.value++;
}
</script>
<style scoped></style>
