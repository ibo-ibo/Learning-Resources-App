<template>
  <teleport to="body">
    <div class="overlay"></div>
    <div class="modal">
      <header class="header">
        <slot name="header">
          <h2 class="title">{{ title }}</h2>
        </slot>
      </header>
      <section class="section">
        <slot></slot>
      </section>
      <div class="actions">
        <slot name="actions"></slot>
      </div>
    </div>
  </teleport>
</template>

<script>
export default {
  props: ['title'],
};
</script>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.75);
  z-index: 10;
}

.modal {
  position: fixed;
  top: 20vh;
  left: 10%;
  width: 80%;
  z-index: 100;
  border-radius: 12px;
  border: none;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 0;
  margin: 0;
  overflow: hidden;
}

.header {
  background-color: #3a0061;
  color: white;
  width: 100%;
  padding: 1rem;
}

header .title {
  margin: 0;
}

.section {
  padding: 1rem;
  background-color: #fff;
}

.actions {
  padding: 1rem;
  display: flex;
  justify-content: flex-end;
  margin: 0;
  background-color: #fff;
}

@media (min-width: 768px) {
  .modal {
    left: calc(50% - 20rem);
    width: 40rem;
  }
}
</style>
