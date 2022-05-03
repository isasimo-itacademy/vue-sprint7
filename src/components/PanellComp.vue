<template>
  <div class="panell">
    <div class="opcio">Pàgines <ButtonCounter :count="tempPag" v-model="tempPag" @increase-by="increaseCountPag" @decrease-by="decreaseCountPag"></ButtonCounter></div>
    <div class="opcio">Idiomes <ButtonCounter :count="tempIdi" v-model="tempIdi" @increase-by="increaseCountIdi" @decrease-by="decreaseCountIdi"></ButtonCounter></div>
  </div>
</template>

<script>
import ButtonCounter from '@/components/ButtonCounter.vue'

export default {
  name: 'PanellComp',
  components: {
    ButtonCounter
  },
  props: ['fillPag', 'fillIdi'],
  data() {
    return { tempPag: this.fillPag, tempIdi: this.fillIdi }
  },
  methods: {
    increaseCountPag() {
      this.tempPag++
      this.$emit('update-var1', this.tempPag)
    },
    decreaseCountPag() {
      this.tempPag--
      this.$emit('update-var1', this.tempPag)
    },
    increaseCountIdi() {
      this.tempIdi++
      this.$emit('update-var2', this.tempIdi)
    },
    decreaseCountIdi() {
      this.tempIdi--
      this.$emit('update-var2', this.tempIdi)
    }
  }
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
  align-items: center;
  margin-top: 10px;
}
</style>