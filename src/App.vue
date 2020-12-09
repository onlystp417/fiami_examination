<template>
  <div id="app">
    <Header></Header>
    <ContentArea></ContentArea>
    <Navegation></Navegation>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import ContentArea from './components/ContentArea.vue';
import Navegation from './components/Navegation.vue';

export default {
  name: 'App',
  components: {
    Header,
    ContentArea,
    Navegation
  }
}
</script>

<style>
*, *::before, *::after {
  box-sizing: border-box;
}

body, h3, p, ul {
  margin: 0;
}

ul {
  list-style: none;
  padding-left: 0;
}

button {
  border: none;
}

button:focus, button:active {
  outline: none;
}
</style>
