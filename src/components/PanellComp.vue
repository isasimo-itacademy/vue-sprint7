<template>
  <div class="panell">
    
    <div class="opcio">Pàgines 
      <ButtonCounter :count="tempPag" v-model="tempPag" @increase-by="increaseCountPag" @decrease-by="decreaseCountPag"></ButtonCounter>
      <button class="boto boto-primari marge-esq" @click="toggle = !toggle, pagines = !pagines">Info</button>
    </div>
    <div class="opcio">Idiomes 
      <ButtonCounter :count="tempIdi" v-model="tempIdi" @increase-by="increaseCountIdi" @decrease-by="decreaseCountIdi"></ButtonCounter>
      <button class="boto boto-primari marge-esq" @click="toggle = !toggle, idiomes = !idiomes">Info</button>
      </div>
    
    <!-- Overlay -->
    <b-overlay variant="dark" show v-show='toggle' no-wrap >
      <template #overlay>        
        <div v-if="pagines" class="mesinfo">
          <p>Indica el número de pàgines que vols que tingui la teva web</p>
          <b-button variant="dark" @click="toggle = !toggle, pagines = !pagines">Tanca</b-button>
        </div>
        <div v-if="idiomes" class="mesinfo">
          <p>Indica el número d'idiomes que vols que tingui la teva web</p>
          <b-button variant="dark" @click="toggle = !toggle, idiomes = !idiomes">Tanca</b-button>
        </div>
      </template>
    </b-overlay>
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
    return { 
      tempPag: this.fillPag,
      tempIdi: this.fillIdi,
      toggle: false,
      pagines: false, 
      idiomes: false
    }
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

.panell, .mesinfo {
  border: 2px solid black;
  border-radius: 10px;
  padding: 16px;
  margin: 16px 0;
}

.mesinfo {
  background-color: rgb(215, 215, 215) !important;
}
.opcio{
  display: flex;
  align-items: center;
  margin-top: 10px;
}
</style>