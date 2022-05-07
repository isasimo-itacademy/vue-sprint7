<template>
  <div>
    <div class="main">
      <h1>Calcula el teu pressupost</h1>

      <div class="basic-input">
        <label for="nom"><strong>Nom del Client</strong></label>
        <input type="text" id="nom" placeholder="Introdueix el teu nom" v-model="nomclient">
      </div>
      <div class="basic-input">
        <label for="presu"><strong>Nom del pressupost</strong></label>
        <input type="text" id="presu" placeholder="Introdueix el nom del pressupost" v-model="nompressupost">
      </div>

      <p><strong>Serveis:</strong></p>
      <div class="opcio">
        <input type="checkbox" id="paginaweb" value=500 v-model="checked" @change="panellObert = !panellObert">
        <label for="paginaweb">Una pàgina Web - 500 €</label>

        <!-- Show component only if checkbox is checked -->
        <PanellComp v-if="panellObert" :fillPag="numPagines" :fillIdi="numIdiomes" @update-var1="updateVar1" @update-var2="updateVar2"></PanellComp>
      </div>
      <div class="opcio">
        <input type="checkbox" id="seo" value=300 v-model="checked">
        <label for="seo">Una consultoria SEO - 300 €</label>
      </div>
      <div class="opcio">    
        <input type="checkbox" id="marketing" value=200 v-model="checked">
        <label for="marketing">Una campanya de Google Ads - 200 €</label>
      </div>

      <p><strong>Preu Total: {{ total }}</strong></p>

      <div class="accions">
        <button class="boto boto-primari" @click="welcome">Anar Enrere</button>
        <button class="boto boto-secondari marge-esq" @click="welcome">Demana Pressupost</button>
      </div>
    </div>
    <div v-if="llistat" class="llistat">
    </div>
  </div>
</template>

<script>
import PanellComp from '@/components/PanellComp.vue'

export default {
  name: 'HomeView',
  components: {
    PanellComp
  },
  data() {
    return {
      checked: [],
      numPagines: '1',
      numIdiomes: '1', 
      panellObert: false,
      llistatObert:false
  }
  },
  computed: {
    total() {
      let serveis = this.checked.reduce((a, b) => parseInt(a) + parseInt(b), 0);
      /* Only count when component is open  */
      if (this.panellObert){
        return serveis + (parseInt(this.numPagines) * parseInt(this.numIdiomes) * 30);
      } else {
        return serveis;
      }
     } 
  },
  methods: {
    updateVar1(e) {
      this.numPagines = e;
    },
    updateVar2(e) {
      this.numIdiomes = e;
    },
    welcome(){
      this.$router.push('/')
    }
  }
}
</script>

<style scoped>
input{
  margin-right: 10px;
}
.opcio {
  margin-bottom: 10px;
}
.accions {
  display: flex;
}
.basic-input{
  display: flex;
  flex-direction: column;
  margin-bottom: 16px;
}
.etiqueta{
  font-size: 14px;
  font-weight: 600;
}

</style>