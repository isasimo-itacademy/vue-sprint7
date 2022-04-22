<template>
  <div class="panell">
      <!-- <ButtonCounter v-model="numPagines" v-on:decrement-quantity="numPagines--" v-on:increment-quantity="numPagines++"/> {{ numPagines }}
      <ButtonCounter v-model="numIdiomes" v-on:decrement-quantity="numIdiomes--" v-on:increment-quantity="numIdiomes++"/> {{ numIdiomes }}
 -->  
  <!-- <ButtonCounter v-model="modelValue" v-on:decrement-quantity="modelValue--" v-on:increment-quantity="modelValue++"/> {{ modelValue }} -->
   <!-- <input
    type="number"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  /> -->

  </div>
</template>

<script>
/* import ButtonCounter from '@/components/ButtonCounter.vue' */

export default {
  name: 'PanellComp',
  components: {
    /* ButtonCounter */
  },
  props: ['modelValue'],
  emits: ['update:modelValue']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.panell {
  border: 2px solid black;
  border-radius: 10px;
  padding: 16px;
  margin: 16px 0;
}
.opcio{
  display: flex;
}
</style>