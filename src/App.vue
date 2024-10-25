<script>
import Header from './components/Header.vue';
import Vuessenger from './components/Vuessenger.vue';
import Footer from './components/Footer.vue';

export default {
  components: {
      Header,
      Vuessenger,
      Footer
  }
}
</script>

<template>
  <Header/>
  <main class="container">
    <Vuessenger />
  </main>
  <Footer/>
</template>