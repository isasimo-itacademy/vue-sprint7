<template> 
    <div class="file">
      <strong>Client:</strong> {{ nomclient }} <strong>Pressupost:</strong> {{ nompresu }} <strong>Total:</strong> {{ total }}
    </div>  
</template>

<script>
export default {
    name: 'PressupostList',
    props: ['nomclient', 'nompresu', 'total']
}
</script>

<style scoped>

.fila {
  border: 1px solid black;
  background-color: white;
  border-radius: 10px;
  padding: 12px;
  margin: 12px 0;
}

</style>