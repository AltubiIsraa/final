<script setup>
import { toRef } from "vue";
const props = defineProps(["user"]);
const User = toRef(props, "user");
</script>
<template>
  <p class="card">
    <p>Email is : {{ User.email }}</p>
    <!-- <p>street is : {{ User.address.street }}</p> -->
  </p>
</template>


<style>
.card {
  box-shadow: 0 4px 8px 0 rgba(255, 255, 255, 0.827);
  transition: 0.3s;
  width: 100%;
  border-radius: 5px;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgb(255, 255, 255);
}

.container {
  padding: 2px 16px;
}
</style>
