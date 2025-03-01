<template>
  <div class="news">
    <ul>
      <li><a href="#">新闻001</a></li>
      <li><a href="#">新闻002</a></li>
      <li><a href="#">新闻003</a></li>
      <li><a href="#">新闻004</a></li>
    </ul>
    <button @click="getNews">获取用户信息</button>
  </div>
</template>

<script setup lang="ts" name="News">
import axios from "axios";

function getNews() {
  axios.get('http://localhost:8888/list').then(
      response => {
        console.log('response', response)
      },
      error => {
        console.log('error', error)
      }
  )
}

</script>

<style scoped>
/* 新闻 */
.news {
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  height: 100%;
}

.news ul {
  margin-top: 30px;
  list-style: none;
  padding-left: 10px;
}

.news li > a {
  font-size: 18px;
  line-height: 40px;
  text-decoration: none;
  color: #64967E;
  text-shadow: 0 0 1px rgb(0, 84, 0);
}

.news-content {
  width: 70%;
  height: 90%;
  border: 1px solid;
  margin-top: 20px;
  border-radius: 10px;
}
</style>