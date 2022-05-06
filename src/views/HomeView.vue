<template>
  <div>
    <h1>Calcula el teu pressupost</h1>
    <p><strong>Què vols fer?</strong></p>

    <div class="opcio">
      <input type="checkbox" id="paginaweb" value=500 v-model="checked" @change="opcions">
      <label for="paginaweb">Una pàgina Web - 500 €</label>

      <!-- Show component only if checkbox is checked -->
      <PanellComp v-if="paginaOberta === true" :fillPag="numPagines" :fillIdi="numIdiomes" @update-var1="updateVar1" @update-var2="updateVar2"></PanellComp>
      <!-- Num Pàgines: {{ numPagines }}
      Num Idiomes: {{ numIdiomes }} -->

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

    <button class="boto" @click="welcome">Anar Enrere</button>

  </div>
</template>

<script>
/* import ButtonCounter from '@/components/ButtonCounter.vue' */
import PanellComp from '@/components/PanellComp.vue'

export default {
  name: 'HomeView',
  components: {
    /* ButtonCounter */
    PanellComp
  },
  data() {
    return {
      checked: [],
      numPagines: '1',
      numIdiomes: '1', 
      paginaOberta: false
  }
  },
  computed: {
    total() {
      let serveis = this.checked.reduce((a, b) => parseInt(a) + parseInt(b), 0);
      /* Only count when component is open  */
      if (this.paginaOberta){
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
    opcions(){
      if(!this.paginaOberta){
        this.paginaOberta = true;
      } else {
        this.paginaOberta = false;
      }
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
</style>