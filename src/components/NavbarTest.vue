<template>
    <div>
        <div id="nav">
            <router-link id="logo-url" to="/">
                <img id="logo" :src="logo" :alt="alt">
            </router-link>
            <router-link class="home" to="/">Fazer Pedido</router-link>
            <router-link class="pedidos" to="/pedidos">Pedidos</router-link>
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: "NavbarTest",
    props: ["logo", "alt"]
})
</script>
<style scoped>
    #nav {
    background-color: #222;
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
  #nav #logo-url {
    margin: auto;
    margin-left: 0;
  }
  #logo {
    width: 40px;
    height: 40px;
  }
  #nav a {
    color: #fcba03;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
  }
  #nav a:hover {
    color: #FFF;
  }
  .home,
  .pedidos {
    font-weight: bold;
  }
</style>