<script>
import axios from 'axios';
import Chat from './Chat.vue';
import MessageInput from './MessageInput.vue';

export default {
  components: {
    Chat,
    MessageInput
  },
  data() {
    return {
      usuarios: [], 
      mensajes: [] 
    };
  },
  async mounted() {
    await this.obtenerUsuarios();
  },
  methods: {
    async obtenerUsuarios() {
      const url = 'https://randomuser.me/api/?results=2';
      try {
        const { data } = await axios.get(url);
        this.usuarios = data.results;
      } catch (error) {
        console.error('Error al obtener los usuarios', error);
      }
    },
    agregarMensaje(mensaje) {
      console.log('Mensaje recibido:', mensaje);
      this.mensajes.push(mensaje);
    }
  }
};
</script>

<template>
  <div>
    <div v-if="usuarios.length === 2">
      <div v-for="(usuario, index) in usuarios" :key="index">
        <img :src="usuario.picture.large" alt="Imagen del usuario" />
        <h2>{{ usuario.name.first }} {{ usuario.name.last }}</h2>
        <MessageInput :usuario="usuario" @enviarMensaje="agregarMensaje" />
      </div>
    </div>
    
    <Chat :mensajes="mensajes" :usuarios="usuarios" />
  </div>
</template>

<style scoped>
img {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  object-fit: cover;
  margin-bottom: 10px;
}
</style>
