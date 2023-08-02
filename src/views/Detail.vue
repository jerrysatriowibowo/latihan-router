<template>
    <center>
    <div v-if="detail == undefined">
        <p>Halaman Tidak Ada</p>
    </div>
    <div v-else>
    <div class="flex-container">
        <h1>Detail {{ detail.nama }}</h1>
        <img class="img" :src="img(detail.img)" alt="Foto">
        <h2>Harga : {{ detail.harga }}</h2>
        <h3>Deskripsi</h3>
        <h4>"{{ detail.des }}"</h4>
    </div>
    </div>
    </center>
</template>
<script>
import { produk } from '../assets/Produk';

export default {
    props: [
        "id_produk",
    ],
    setup(props)
    {
        const detail = produk["produk"].find(function(item) {
            return item.id == props.id_produk;
        });

        const img = (NamaFoto) => {
            return '../src/assets/picture/' + NamaFoto + '';
        }

        return{
            detail,
            img
        }
    }
}
</script>
<style>
.img{
    width: 450px;
    height: 420px;
}
h1{
    color: red;
}
h2{
    color: red;
}
h4{
    color: black;
}
h3{
    color: black;
}
</style>