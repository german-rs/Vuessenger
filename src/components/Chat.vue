<template>
    <div>
      <h2>Chat</h2>
      <div v-for="(mensaje, index) in mensajes" :key="index">
        <div 
          :class="{'nombre-usuario1': esUsuario1(mensaje.usuario), 'nombre-usuario2': esUsuario2(mensaje.usuario)}"
          class="nombre-usuario">
          <strong>{{ mensaje.usuario.name.first }} {{ mensaje.usuario.name.last }}</strong>
        </div>
        <div 
          :class="{'mensaje-usuario1': esUsuario1(mensaje.usuario), 'mensaje-usuario2': esUsuario2(mensaje.usuario)}"
          :style="{ backgroundColor: mensaje.color }" 
          class="texto-mensaje">
          {{ mensaje.texto }}
        </div>
      </div>
    </div>
  </template>
  
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
    esUsuario2(usuario) {
      return usuario === this.usuarios[1];
    }
  }
};
</script>

<style scoped>
.nombre-usuario1 {
  text-align: left;
  margin-right: auto;
  max-width: 60%;
}

.mensaje-usuario1 {
  text-align: left;
  margin-right: auto;
  padding: 10px;
  border-radius: 10px;
  max-width: 60%;
}

.nombre-usuario2 {
  text-align: right;
  margin-left: auto;
  max-width: 60%;
}

.mensaje-usuario2 {
  text-align: right;
  margin-left: auto;
  padding: 10px;
  border-radius: 10px;
  max-width: 60%;
}

.nombre-usuario {
  font-weight: bold;
  margin-bottom: 5px;
}

.texto-mensaje {
  padding: 10px;
  border-radius: 10px;
}

div {
  margin: 10px 0;
  padding: 10px;
  border-radius: 5px;
}
</style>