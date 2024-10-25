<script>
export default {
props: {
    modelValue: String
},
methods: {
    actualizarColor(evento) {
    this.$emit('update:modelValue', evento.target.value);
    }
}
};
</script>

<template>
    <input type="color" :value="modelValue" @input="actualizarColor" />
</template>

<style scoped>
input{
    width: 90%;
    margin: 0;
}
</style>