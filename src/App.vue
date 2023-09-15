<template>
  <div>
    <NavbarTest :logo="logo_src" :alt="app_name"/>
    <div>
      <router-view></router-view>
    </div>
      

    <FooterTest/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import NavbarTest from './components/NavbarTest.vue';
import FooterTest from './components/FooterTest.vue';

export default defineComponent({
  data: function(){
    return {
      logo_src: "/img/logo.png",
      app_name: "Monte Seu Burger"
    }
  },
  components: {
    NavbarTest,
    FooterTest
  }
})

</script>

<style>
* {
    font-family: Helvetica;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  .main-container {
    margin: 50px;
    min-height: 150px;
  }

  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222;
  }
</style>
