<template>
    <div class="message-container">
      <p>{{ msg }}</p>
    </div>
  </template>
  
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: "MessageTest",
  props: {
    msg: String
  }
})
</script>
  
  <style scoped>
    .message-container {
      color: #004085;
      background-color: #cce5ff;
      border: 2px solid #b8daff;
      border-radius: 5px;
      padding: 10px;
      max-width: 400px;
      margin: 30px auto;
    }
  </style>