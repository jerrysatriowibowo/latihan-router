<template>
    <form @submit.prevent="onSubmit">
        <label>email: </label>
        <input v-model="email" placeholder="email" /> <br>

        <label>name: </label>
        <input v-model="name" placeholder="First Name" /> <br>

        <label>last name: </label>
        <input v-model="lastName" placeholder="Last Name" /> <br>

        <label>nomor identitas:</label>
         <input v-model="nomorIdentitas" placeholder="nomor identitas" /> <br>

        <label>jenis kelamin: </label>

        pria <input type="radio" value="pria" v-model="jenisKelamin" /> | wanita <input type="radio" value="wanita" v-model="jenisKelamin" /> <br>

        alamat: <textarea v-model="about"></textarea> <br>

        <input type="submit" value="Simpan" class="btn btn-block" />

        <p></p>
    </form>
</template>
<script>
import { onMounted } from 'vue';

export default {
    name : 'Register',
    data (){

        onMounted(() => {
            context.emit("id-menu", 6)
        })

        return {
            email : '',
            name : '',
            lastName : '',
            nomorIdentitas : '',
            jenisKelamin : '',
        }
    },
    methods : {
        onSubmit(){
            console.log('email :', this.email);
            console.log('name :', this.name);
            console.log('lastName :', this.lastName);
            console.log('nomorIdentitas :', this.nomorIdentitas);
            console.log('jenisKelamin :', this.jenisKelamin);
        }
    }
}
</script>