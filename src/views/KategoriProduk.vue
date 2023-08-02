<template>
    <center><h1>Daftar Produk {{ NamaKategori }}</h1>
    <div class="flex-container">
        <div v-for="produk in data" :key="produk.id" class="card">
            <img class="img" :src="img(produk.img)" alt="Foto">
        <router-link class="container" :to="{ name : 'Detail', params:{id_produk : produk.id}}">
            <h4>{{ produk.nama }}</h4>
        </router-link>
    </div>
    </div></center>
  </template>
<script>
import { computed } from 'vue';
import { produk } from '../assets/Produk';
import { kategori } from '@/assets/Kategori';

export default {
    props: [
        "id_kategori",
    ],
    setup(props){
        const detail = kategori["kategori"].find(function(item) {
            return item.id == props.id_kategori
        });

        const data = produk["produk"].filter(function(a){
            return detail.id == a.id_kategori
        });

        const NamaKategori = computed(() => {
            const Cari = kategori.kategori.find((item) => item.id == props.id_kategori)
            return Cari ? Cari.nama : ''
        })

        const img = (NamaFoto) => {
            return '../src/assets/picture/' + NamaFoto + '';
        }
        
        return{
            detail,
            data,
            NamaKategori,
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
    box-shadow: 0 20px 20px 0 grey;
    transition: 0.1s;
    margin: 10px;
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