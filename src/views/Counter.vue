<template>
  <center>
    <div id="app">
      <div class="counter">
        {{ counter }} 
      </div>
      <button @click="increment" class="increment"> Tambah </button>
      <button @click="decrement" class="decrement"> Kurang </button>
    </div>
  </center>
</template>
<script>
export default {
    methods: {
      increment() {
        this.$store.commit('increment')
      },
      decrement() {
        this.$store.commit('decrement')
      },
    }, 
    computed: {
      counter() {
        return this.$store.getters.getCounter
      },
    },
  };
</script>
<style scoped>
#app {
  width: 30%;
  margin: 100px auto;
  background: rgb(0, 0, 0);
  padding: 15px;
}
.counter {
  width: 70%;
  padding: 50px 5px;
  margin: 20px auto;
  background: rgb(255, 255, 255);
  color:#000000;
  font-size: 100px;
}
button {
  border: 0;
  padding: 13px 45px;
  font-weight: bold;
  margin-bottom: 20px;
}
.increment {
  background: #00a724;
  color: #000000;
}
.increment:hover {
  transition: .7s;
  opacity: 0.8;
  cursor: pointer;
}
.decrement {
  background: #ff1900;
  color: #000000;
}
.decrement:hover {
  transition: .7s;
  opacity: 0.9;
  cursor: pointer;
}
</style>