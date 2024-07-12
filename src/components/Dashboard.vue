<template>
  <div id="burger-table" v-if="burgers">
      <div>
        <div id="burger-table-heading">
          <div class="order-id">#:</div>
          <div>Cliente:</div>
          <div>Pão:</div>
          <div>Carne:</div>
          <div>Opcionais:</div>
          <div>Ações:</div>
        </div>
      </div>
      <div id="burger-table-rows">
        <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
          <div class="order-number">{{ burger.id }}</div>
          <div>{{ burger.nome }}</div>
          <div>{{ burger.pao }}</div>
          <div>{{ burger.carne }}</div>
          <div>
            <ul v-for="(opcional, index) in burger.opcionais" :key="index">
              <li>{{ opcional }}</li>
            </ul>
          </div>
          <div>
            <select name="status" class="status" @change="updateBurger($event, burger.id)">
              <option :value="s.tipo" v-for="s in status" :key="s.id" :selected="burger.status == s.tipo">
                {{ s.tipo }}
              </option>
            </select>
            <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
          </div>
        </div>
      </div>
  </div>
  <div v-else>
    <h2>Não há pedidos no momento!</h2>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
interface Burger {
  id: number;
  nome: string;
  pao: string;
  carne: string;
  opcionais: string[];
  status: string;
}
interface Status {
  id: number;
  tipo: string;
}
export default defineComponent({
  name: "Dashboard",
  setup() {
    const burgers = ref<Burger[] | null>(null);
    const status = ref<Status[]>([]);
    const getPedidos = async () => {
      const req = await fetch("http://localhost:3000/burgers");
      const data = await req.json();
      burgers.value = data;
      await getStatus();
    };
    const getStatus = async () => {
      const req = await fetch("http://localhost:3000/status");
      const data = await req.json();
      status.value = data;
    };
    const deleteBurger = async (id: number) => {
      await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE",
      });
      await getPedidos();
    };
    const updateBurger = async (event: Event, id: number) => {
      const option = (event.target as HTMLSelectElement).value;
      const dataJson = JSON.stringify({ status: option });
      await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });
    };
    onMounted(() => {
      getPedidos();
    });
    return {
      burgers,
      status,
      deleteBurger,
      updateBurger
    };
  },
});
</script>
<style scoped>
    #burger-table {
      max-width: 1200px;
      margin: 0 auto;
    }
    #burger-table-heading,
    #burger-table-rows,
    .burger-table-row {
      display: flex;
      flex-wrap: wrap;
    }
    #burger-table-heading {
      font-weight: bold;
      padding: 12px;
      border-bottom: 3px solid #333;
    }
    .burger-table-row {
      width: 100%;
      padding: 12px;
      border-bottom: 1px solid #CCC;
    }
    #burger-table-heading div,
    .burger-table-row div {
      width: 19%;
    }
    #burger-table-heading .order-id,
    .burger-table-row .order-number {
      width: 5%;
    }
    select {
      padding: 12px 6px;
      margin-right: 12px;
    }
    .delete-btn {
      background-color: #222;
      color:#fcba03;
      font-weight: bold;
      border: 2px solid #222;
      padding: 10px;
      font-size: 16px;
      margin: 0 auto;
      cursor: pointer;
      transition: .5s;
      border-radius: 5px;
    }
    .delete-btn:hover {
      background-color: transparent;
      color: #222;
    }
</style>