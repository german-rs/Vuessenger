<script>
export default {
  props: {
    mensajes: Array,
    usuarios: Array
  },
  methods: {
    esUsuario1(usuario) {
      return usuario === this.usuarios[0];
    },
    obtenerEstiloMensaje(usuario) {
      const esUsuario1 = this.esUsuario1(usuario);
      return {
        textAlign: esUsuario1 ? 'left' : 'right',
        marginRight: esUsuario1 ? 'auto' : '0',
        marginLeft: esUsuario1 ? '0' : 'auto',
        backgroundColor: usuario.color,
      };
    }
  }
}
</script>

<template>
  <div class="chat-container">
    <div class="chat-mensajes">
      <div v-for="(mensaje, index) in mensajes" :key="index">
        <div :style="{ textAlign: esUsuario1(mensaje.usuario) ? 'left' : 'right' }" class="nombre-usuario">
          <strong>{{ mensaje.usuario.name.first }} {{ mensaje.usuario.name.last }}</strong>
        </div>
        <div :style="obtenerEstiloMensaje(mensaje.usuario)" class="texto-mensaje">
          {{ mensaje.texto }}
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.chat-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.chat-mensajes {
  width: 400px;
  height: 400px;
  overflow-y: auto;
  padding: 10px;
  box-sizing: border-box;
  border-radius: 15px; 
  border: 2px solid transparent;
  border-image: linear-gradient(to right, #42d392, #549ced) 2 2;
  background-color: var(--color-gris50);
}

.nombre-usuario {
  font-weight: bold;
  margin-bottom: 5px;
  font-size: 12px;
  padding-top: 1em;
  color: var(--color-gris600);
}

.texto-mensaje {
  padding: 10px;
  border-radius: 10px;
  max-width: 60%;
}
</style>
