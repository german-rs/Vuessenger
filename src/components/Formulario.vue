<script>
</script>
<template>
    <div class="contenedor__formulario">
        <label for="colorPicker">Elige un color:</label>
        <input type="color" id="colorPicker" name="colorPicker">
       <textarea></textarea> 
       <button>Enviar</button>
    </div>
</template>
<style scoped>
.contenedor__formulario{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    gap: .5em; 
}
</style>