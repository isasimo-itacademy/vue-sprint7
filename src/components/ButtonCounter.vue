<template>
  <div class="counter">
    <button class="boto-square" @click="$emit('decreaseBy')" v-bind:disabled="count<=1">-</button>
    <input
    type="number" min="1"
    :value="count"
    @input="$emit('update:count', $event.target.value)"
  />
    <button class="boto-square" @click="$emit('increaseBy')">+</button>
  </div>
</template>

<script>
export default {
  name: 'ButtonCounter',
  props: ['count'],
  emits: ['update:count','increaseBy','decreaseBy']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.counter {
  margin-left: 10px;
}
input {
  background-color: white;
  border: none;
  border-radius: 6px;
  margin: 0 8px;
  padding: 8px 0;
  width: 40px;
  text-align: center;
}
</style>