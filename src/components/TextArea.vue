<script>
export default {
  props: {
    modelValue: String
  },
  methods: {
    updateValue(event) {
      this.$emit('update:modelValue', event.target.value);
    }
  }
};
</script>

<template>
    <textarea :value="modelValue" @input="updateValue"></textarea>
</template>

<style scoped>
textarea{
    width: 100%;
    height: auto;
    padding: .4em;
    border-radius: 8px;
    border: 1px solid var(--color-gris400);
    font-family: 'Inter', sans-serif;
    font-size: 1em;
}
</style>