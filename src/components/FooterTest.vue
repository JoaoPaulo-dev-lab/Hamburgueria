<template>
    <div id="footer">
      <p>Monte Seu Burger &copy; <span id="year"></span></p>
    </div>
  </template>
  
  <script>
  export default {
    name: "FooterTest",

    
    methods: {
      getFullYear(){
        const year = document.getElementById('year')
        const anoAtual = new Date();
        year.innerHTML = anoAtual.getFullYear()
      }
    },
    mounted(){
      this.getFullYear()
    }
  }
  </script>
  
  <style scoped>
    #footer {
      height: 130px;
      background-color: #222;
      border-top: 4px solid #111;
      color: #fcba03;
      display: flex;
      align-items: center;
      justify-content: center;
      bottom: 0;
      width: 100%;
    }
  </style>