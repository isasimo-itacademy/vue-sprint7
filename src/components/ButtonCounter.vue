<template>
  <div class="counter">
    <button class="boto-square" v-on:click="$emit('decrement-quantity');" v-bind:disabled="modelValue<=1">-</button>
    <input
        type="number" min="1"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
    />
    <button class="boto-square" v-on:click="$emit('increment-quantity');">+</button>
  </div>
</template>

<script>
export default {
    name: 'ButtonCounter',
    props: ['modelValue'],
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