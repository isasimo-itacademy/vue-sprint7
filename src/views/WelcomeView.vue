<template>
  <div class="welcome">
    <h1>Benvingudes a Pressupostland</h1>
    <button class="boto" @click="home">Demana Pressupost</button>
  </div>
</template>

<script>

export default {
  name: 'WelcomeView',
  methods: {
    home(){
      this.$router.push('/home')
    }
  }
}
</script>