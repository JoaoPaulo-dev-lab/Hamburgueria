<template>
  <div>
    <BannerTest/>
    <div class="main-container">
      <h1>Preencha os campos abaixo:</h1>
    </div>
    <BurgerForm/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BannerTest from '@/components/BannerTest.vue';
import BurgerForm from '@/components/BurgerForm.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    BannerTest,
    BurgerForm
  }
})
</script>
