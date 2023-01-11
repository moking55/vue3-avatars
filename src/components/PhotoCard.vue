<script setup>
import LikeAndSad from "./LikeAndSad.vue";
defineProps({
  image: String,
  description: String,
  background: String,
});
</script>
<template>
  <div class="col-md-4">
    <div class="card mb-4 shadow-sm">
      <img
        class="card-img-top"
        height="225"
        :style="'background: #' + background"
        :src="image"
      />
      <div class="card-body">
        <p class="card-text">{{ description }}<br /></p>
        <div class="d-flex justify-content-between align-items-center">
          <div class="btn-group">
            <LikeAndSad />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
