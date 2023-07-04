<template>
  <button>
    <slot></slot>
  </button>
</template>

<style scoped>
button {
  border: 1px solid #360032;
  background-color: #360032;
  color: white;
  padding: 1rem 3rem;
  cursor: pointer;
  border-radius: 12px;
}

button:hover,
button:active {
  background-color: #5c0556;
  border-color: #5c0556;
}
</style>
