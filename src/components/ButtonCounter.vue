<template>
  <div class="counter">
    <button class="boto-square" @click="resta">-</button>
    A net "anet": {{ anet }}
    <button class="boto-square" @click="suma">+</button>
  </div>
</template>

<script>
export default {
  name: 'ButtonCounter',
  props: ['net'],
  data() {
    return { anet: this.net }
  },
  methods: {
    suma(){
      this.$emit('increaseBy', this.anet++)
      console.log(this.anet);
    },
    resta(){
      this.$emit('reduceBy', this.anet--)
      console.log(this.anet);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.counter {
  margin: 12px 20px
}
input {
  background-color: white;
  border: none;
  border-radius: 6px;
  margin: 0 4px;
  padding: 6px 0;
  width: 40px;
  text-align: center;
}
</style>