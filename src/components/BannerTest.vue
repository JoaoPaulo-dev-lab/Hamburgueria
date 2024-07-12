<template>
    <div id="main-banner">
        <h1>Monte Seu Burger</h1>
    </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
    name: "BannerTest"
})
export default class BannerTest extends Vue{}

</script>

<style scoped lang="css">
    #main-banner{
        background-image: url('https://raw.githubusercontent.com/matheusbattisti/curso_vue_yt/620a04ebb9caddd742aac42e2bbcccd42e0235a2/18_projeto/public/img/burger.jpg');
        background-position: 0 -250px;
        background-size: cover;
        height: 500px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }

    #main-banner h1{
        color: #fff;
        text-align: center;
        font-size: 60px;
        background-color: #222;
        padding: 20px 40px;
    }

    @media screen and (max-width: 1083px) {
        #main-banner{
            background-repeat: no-repeat;
            background-position: center;
            display: flex;
        }

        #main-banner h1{
            font-size: 32px;
            padding: 12px 24px;
        }
    }
</style>