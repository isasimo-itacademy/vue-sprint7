<template>
  <div class="home">
    <div class="main">
      <h1>Calcula el teu pressupost</h1>

      <div class="basic-input">
        <label for="nom"><strong>Nom del Client</strong></label>
        <input type="text" id="nom" v-model="nomclient" placeholder="Introdueix el teu nom">
      </div>
      <div class="basic-input">
        <label for="presu"><strong>Nom del pressupost</strong></label>
        <input type="text" id="presu" v-model="nompresu" placeholder="Introdueix el nom del pressupost">
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
        <button class="boto boto-secondari marge-esq" @click="pressuposta()">Demana Pressupost</button>
      </div>
    </div>
    <div v-if="llistatObert" class="llistat">
      <h3>Pressupostos rebuts</h3>
      <PressupostList v-for="(item) in items" :key="item.id" :nomclient="item.nomclient" :nompresu="item.nompresu" :total="item.total"></PressupostList>
    </div>
  </div>
</template>

<script>
import PanellComp from '@/components/PanellComp.vue'
import PressupostList from '@/components/PressupostList.vue'

export default {
  name: 'HomeView',
  components: {
    PanellComp, 
    PressupostList
  },
  data() {
    return {
      checked: [],
      numPagines: '1',
      numIdiomes: '1', 
      panellObert: false,
      llistatObert: false,
      nomclient:'',
      nompresu:'',
      items: [],
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
    },
    pressuposta(){
      this.llistatObert = true;

      let new_pressu = {}; 
      new_pressu.nomclient = this.nomclient;
      new_pressu.nompresu = this.nompresu;
      new_pressu.total = this.total;
      this.items.push(new_pressu);
      console.log(this.items);
    }
  }
}
</script>

<style scoped>

.home {
  display: flex;
  justify-content: space-between;
}
.main {
  width: 55%;
}
.llistat{
  width: 40%;
}

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

</style>