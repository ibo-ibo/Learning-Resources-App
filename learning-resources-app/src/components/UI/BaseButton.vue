<template>
  <button :class="mode"><slot></slot></button>
</template>

<script>
export default {
  props: ['mode'],
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #610028;
  border: 1px solid #610028;
  border-radius: 8px;
  color: white;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #410011;
  border-color: #410011;
}

.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>
