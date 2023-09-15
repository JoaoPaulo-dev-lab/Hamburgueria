<template>
  <div>
    <div class="main-container">
      <h1>Gerenciar pedidos:</h1>
      <Dashboard />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Dashboard from '@/components/Dashboard.vue';

export default defineComponent({
  name: "Pedidos",
  components: {
    Dashboard
  }
})
</script>
