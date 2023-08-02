<template>
    <center>
    <h1>Halaman Kategori</h1>
    <div class="flex-container">
        <div v-for="kategori in state" :key="kategori.id" class="card">
            <img class="img" :src="img(kategori.img)" alt="Foto">
        <router-link class="container" :to="{ name : 'KategoriProduk', params:{id_kategori : kategori.id}}">
            <h4>{{ kategori.nama }}</h4>
        </router-link>
        </div>
    </div>
    </center>
</template>
<script>
import { onMounted, reactive } from 'vue';
import { kategori } from '@/assets/Kategori';

export default{
    setup(props, context){

        const state = reactive(kategori["kategori"]);

        onMounted(() => {
            context.emit("id-menu",5)
        });

        const img = (NamaFoto) => {
            return '../src/assets/picture/' + NamaFoto + '';
        }

        return{
            state,
            img
        }
    }
}
</script>
<style scoped>
.flex-container {
    display: flex;
}
.card {
    box-shadow: 0 10px 10px 0 grey;
    transition: 0.1s;
    margin: 26px;
    min-width: 200px;
    cursor: pointer;
}
.card:hover {
    box-shadow: 0 8px 16px 0 aqua;
}
.container {
    padding: 2px 16px;
}
.img{
    width: 150px;
    height: 170px;
}
</style>