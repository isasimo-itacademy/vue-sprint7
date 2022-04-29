<template>
  <div class="panell">
    <ButtonCounter :net="envianet"></ButtonCounter>
    A fill "envianet": {{ envianet }} <br/>
    A fill "getnet": {{ getnet }} <br/>

  </div>
</template>

<script>
import ButtonCounter from '@/components/ButtonCounter.vue'

export default {
  name: 'PanellComp',
  components: {
    ButtonCounter
  },
  props: ['fill'],
  data() {
    return { envianet: this.fill }
  },
  emits: ['getnet']
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