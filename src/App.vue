<template>
  <nav>
    <router-link to="/">Welcome</router-link> |
    <router-link to="/home">Home</router-link>
  </nav>
  <router-view class="content"/>

</template>

<style>
html {
  padding: 0;
  margin: 0;
  background-color: #dbe9e3;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #dbe9e3;
  color: #334456;
  padding: 30px;
  margin: 0;
}
.content {
  padding: 0 30px;
}
nav {
  padding: 30px;
}
nav a {
  font-weight: bold;
  color: #2c3e50;
}
nav a.router-link-exact-active {
  color: #42b983;
}

.marge-esq {
  margin-left: 16px;
}
.marge-dre {
  margin-right: 16px;
}

.boto-primari {
  background-color: #2bd588;
  color: #2c3e50;
}

.boto-secondari {
  background-color: #2c3e50;
  color:  #2bd588;
}

.boto {
  border: none;
  border-radius: 6px;
  padding: 8px 12px;
  font-weight: 600;
}

.boto-square {
  background-color: #2bd588;
  color: #2c3e50;
  border: none;
  border-radius: 6px;
  padding: 8px;
  min-width: 40px;
  font-weight: 600;
}

.boto-primari:hover, .boto-square:hover {
  background-color: #47e49e;
  cursor: pointer;
}

.accions {
  display: flex;
  margin-bottom: 16px;
}

</style>