<template>
  <div>
    <button v-on:click="$emit('decrement-quantity');" v-bind:disabled="modelValue<=1">-</button>
    <input
        type="number" min="1"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
    />
    <button v-on:click="$emit('increment-quantity');">+</button>
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
</style>