<script setup>
import { ref, onErrorCaptured } from "vue";
import PostsCardVue from "./PostsCard.vue";
import UserCardVue from "./UserCard.vue";
const SelectedPos = ref(null);
const SelectedUser = ref({});
const response = ref({});
const responsepost = ref({});

// adding delay

await new Promise((resolve) => {
  setTimeout(() => {
    resolve();
  }, 1000);
});

onErrorCaptured((err) => {
  // error processing
});

response.value = await (
  await fetch("https://jsonplaceholder.typicode.com/users/" )
).json();



async function onChange() {
  console.log("hi");

  responsepost.value = await (
  await fetch(`https://jsonplaceholder.typicode.com/users/${SelectedUser.value.id}/posts`)
  ).json();
}
</script>

<template>
  <select v-model="SelectedUser" @change="onChange">
    <option v-for="item in response" v-bind:key="item.id" :value="item">
      {{ item.name }}
    </option>
  </select>

  
  <br/><br/><br/><br/>
  <div v-for="item in responsepost" v-bind:key="item.id" :value="item">
    <p class="card">Title: {{ item.title }}</p>
    <!-- <p>Body: {{ item.body }}</p> -->

  </div>
  <!-- <UserCardVue :user="SelectedUser"/> -->
  
  <br/><br/><br/><br/>

</template>
<style>
.card {
  box-shadow: 0 4px 8px 0 rgba(255, 255, 255, 0.827);
  transition: 0.3s;
  width: 40%;
  border-radius: 5px;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgb(255, 255, 255);
}

.container {
  padding: 2px 16px;
}
</style>
