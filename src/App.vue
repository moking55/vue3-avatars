<script setup>
import { ref } from "vue";
import PhotoCard from "./components/PhotoCard.vue";
import randomnameThai from "@opecgame/randomname-thai";

function random_bg_color(seed) {
  return Math.floor(Math.abs(Math.sin(seed) * 16777215)).toString(16);
}
function ranInt(max) {
  return Math.floor(Math.random() * max);
}
function add_avatar() {
  data.value.push({
    description: randomnameThai().nickname,
    img_seed: ranInt(100),
    background: random_bg_color(ranInt(100)),
  });
}
function remove_avatar() {
  data.value.pop(0);
}

let data = ref([]);
</script>

<template>
  <header>
    <div id="navbarHeader" class="collapse bg-dark">
      <div class="container">
        <div class="row">
          <div class="col-sm-8 col-md-7 py-4">
            <!-- Start: h4 about -->
            <h4 class="text-white">หลักการทำงาน</h4>
            <!-- End: h4 about -->
            <!-- Start: paragraph -->
            <div class="text-muted">
              เมื่อคลิ๊ก เพิ่ม Avatar จะทำการเพิ่มในส่วนของ Array
              เข้าไปยังตัวแปร data แล้วทำการ v-for ออกมา โดยแต่ละ props
              จะมีการทำงานดังนี้
              <br />
              <br />
              image: จะเป็นการดึงรูป Avatar จาก api.dicebear.com และทำการสุ่ม
              Seed เพื่อ
              <br />
              description: เป็นการสุ่มชื่อไทยโดยใช้ Module
              @opecgame/randomname-thai
              <br />
              background: เป็นการสุ่มสีพื้นหลังโดยการใช้ seed ที่สุ่มมาอีกที
              <br />
              <br />
              และเมื่อคลิ๊ก ลบ Avatar จะเป็นการลบรูปภาพจาก Array
              ที่อยู่ด้านหลังสุด แต่ที่เห็นข้อมูลโดนลบด้านหน้าเพราะใช้
              .reverse()
              <br />
              <br />
              Lib ที่ใช้ลงเพิ่มเติม
              <ul>
                <li>
                  <a
                    href="https://www.npmjs.com/package/@opecgame/randomname-thai"
                    >@opecgame/randomname-thai</a
                  >
                </li>
              </ul>
            </div>
            <!-- End: paragraph -->
          </div>
          <div class="col-sm-4 offset-md-1 py-4">
            <!-- Start: h4 contact -->
            <h4 class="text-white">Source Code</h4>
            <!-- End: h4 contact -->
            <!-- Start: lists unordered -->
            <ul class="list-unstyled">
              <li>
                <a href="//github.com/moking55" class="text-white">Github</a>
              </li>
            </ul>
            <!-- End: lists unordered -->
          </div>
        </div>
      </div>
    </div>
    <div class="navbar navbar-dark bg-dark shadow-sm w-100">
      <div class="container d-flex justify-content-between">
        <a class="navbar-brand d-flex align-items-center" href="#"
          ><i class="fa fa-camera"></i><strong>&nbsp;Avatar Album</strong></a
        ><button
          class="btn navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarHeader"
          aria-controls="navbarHeader"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <i class="navbar-toggler-icon"></i>
        </button>
      </div>
    </div>
  </header>
  <main role="main">
    <section class="jumbotron mb-0 text-center py-5">
      <div class="container">
        <h1>Avatar Album Examples</h1>
        <p class="lead text-muted">
          <br />
          คลิ๊กที่ปุ่ม เพิ่ม Avatar เพื่อเพิ่มคอลเล็คชั่นไปยังอัลบั้ม
          <br />
        </p>
        <div>
          <div class="btn-group" role="group" aria-label="btn group">
            <button class="btn btn-success my-2" @click="add_avatar">
              <i class="fas fa-plus fa-xs"></i> เพิ่ม Avatar
            </button>
            <button class="btn btn-danger my-2" @click="remove_avatar">
              <i class="fas fa-trash fa-xs"></i> ลบ Avatar
            </button>
          </div>
          <br />
          <small>ขณะนี้มี {{ data.length }} รูป</small>
        </div>
      </div>
    </section>
    <div class="album py-5 bg-light">
      <div class="container">
        <div class="row">
          <!-- <div class="col-md-4">

            <div class="card mb-4 shadow-sm">
              <img
                class="bd-placeholder-img"
                width="100%"
                height="225"
                src="assets/img/varun-mama.jpg?h=84121e32fea1d516cf6551992dab13be"
              />
              <div class="card-body">
                <p class="card-text">
                  This is a wider card with supporting text below as a natural
                  lead-in to additional content. This content is a little bit
                  longer.<br />
                </p>
                <div class="d-flex justify-content-between align-items-center">
                  <div class="btn-group">
                    <button
                      type="button"
                      class="btn btn-sm btn-outline-secondary"
                    >
                      View
                    </button>
                    <button
                      type="button"
                      class="btn btn-sm btn-outline-secondary"
                    >
                      Edit
                    </button>
                  </div>
                  <small>9 min</small>
                </div>
              </div>
            </div>
          </div> -->
          <PhotoCard
            v-for="(value, index) in data.slice().reverse()"
            :image="
              'https://api.dicebear.com/5.x/adventurer/svg?seed=' +
              value.img_seed
            "
            :description="value.description"
            :background="value.background"
            :key="index"
          />
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.navbar-toggler {
  padding: 0.25rem 0.75rem;
  font-size: 1.25rem;
  line-height: 1;
  background-color: transparent;
  border: 1px solid transparent;
  border-radius: 0.25rem;
}

.navbar-toggler:focus,
.navbar-toggler:hover {
  text-decoration: none;
}

.navbar-toggler-icon {
  display: inline-block;
  width: 1.5em;
  height: 1.5em;
  vertical-align: middle;
  content: "";
  background: center center no-repeat;
  background-size: 100% 100%;
}
</style>
