<script>
  export default {
    props: {
      usuario: Object
    },
    data() {
      return {
        texto: '', 
        color: '#ffffff'
      };
    },
    methods: {
      enviarMensaje() {
        if (this.texto.trim()) {
          const mensaje = {
            usuario: this.usuario,
            texto: this.texto,
            color: this.color
          };
          this.$emit('enviarMensaje', mensaje); 
          this.texto = ''; 
          this.color = '#ffffff';
        }
      }
    }
  };
</script>

<template>
  <div>
    <input v-model="texto" placeholder="Escribe un mensaje..." />
    <input type="color" v-model="color" />
    <button @click="enviarMensaje">Enviar</button>
  </div>
</template>
  
<style scoped>
input {
  margin-right: 10px;
}
</style>