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
    }
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
        console.error(error);
      }
    },
    agregarMensaje(mensaje) {
      this.mensajes.push(mensaje);
    }
  },
  computed: {
    informacionUsuarios() {
      if (this.usuarios.length < 2) return null;
      
      return this.usuarios.map(usuario => ({
        name: `${usuario.name.first} ${usuario.name.last}`,
        img: usuario.picture.large,
        data: usuario
      }));
    }
  }
}
</script>

<template>
  <div class="contenedor__vuessenger">
    <div v-if="informacionUsuarios" class="contenedor__usuario">
      <img :src="informacionUsuarios[0].img" alt="Imagen del usuario" />
      <h3>{{ informacionUsuarios[0].name }}</h3>
      <MessageInput :usuario="informacionUsuarios[0].data" @enviarMensaje="agregarMensaje" />
    </div>

    <Chat :mensajes="mensajes" :usuarios="usuarios" />

    <div v-if="informacionUsuarios" class="contenedor__usuario">
      <img :src="informacionUsuarios[1].img" alt="Imagen del usuario" />
      <h3>{{ informacionUsuarios[1].name }}</h3>
      <MessageInput :usuario="informacionUsuarios[1].data" @enviarMensaje="agregarMensaje" />
    </div>
  </div>
</template>

<style scoped>
.contenedor__vuessenger{
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  padding: 1em; 
  gap: 1em;
  margin: 1em 0;
}

img {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  object-fit: cover;
  margin-bottom: 10px;
}

.contenedor__usuario{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 1em;
  width: 100%;
  max-width: 400px;
  border: 1px solid var(--color-verde);
  border-radius: 10px;
}
</style>