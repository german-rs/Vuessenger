<script>
import TextArea from './TextArea.vue';
import Button from './Button.vue';
import Colour from './Colour.vue';
export default {
  components:{
    TextArea,
    Button,
    Colour
  },
  props: {
    usuario: Object
  },
  data() {
    return {
      texto: '', 
      color: this.usuario.color || '#ffffff' 
    };
  },
  watch: {
    color(newColor) {
      this.usuario.color = newColor; 
    }
  },
  methods: {
    enviarMensaje() {
      if (this.texto.trim()) {
        const mensaje = {
          usuario: this.usuario,
          texto: this.texto,
          color: this.usuario.color 
        };
        this.$emit('enviarMensaje', mensaje);
        this.texto = ''; 
      }
    }
  }
}
</script>

<template>
  <div class="contenedor__formulario">
    <Colour v-model="color"/>
    <TextArea v-model="texto" @keyup.enter="enviarMensaje" />
    <Button @click="enviarMensaje"/>
  </div>
</template>
  
<style scoped>
  .contenedor__formulario {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    gap: .5em;
    padding: 1em;
  }
</style>