<template>
    <center>
    <h1>Produk Page</h1>
    <div class="flex-container">
        <div v-for="produk in jual" :key="produk.id" class="card">
            <img class="img" :src="img(produk.img)" alt="Foto">
        <router-link class="container" :to="{ name : 'Detail', params:{id_produk : produk.id}}">
            <h4>{{ produk.nama }}</h4>
        </router-link>
    </div>
    </div>
    </center>
</template>
<script>
import { onMounted, reactive } from 'vue';
import { produk } from '@/assets/Produk';

export default{
    setup(props,context){

        const jual = reactive(produk["produk"]);

        onMounted(() => {
            context.emit("id-menu",4)
        });

        const img = (NamaFoto) => {
            return '../src/assets/picture/' + NamaFoto + '';
        }

        return{
            jual,
            img
        }
    }
}
</script>
<style scoped>
.flex-container {
    display: flex;
    flex-wrap: wrap;
}
.card {
    box-shadow: 0 20px 20px 0 grey;
    transition: 0.1s;
    margin: 55px;
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
    height: 160px;
}
</style>