<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  element: {
    type: Object,
    required: true
  }
})
</script>
<template>
<div class="modal" :class="{ 'is-active': isActive }">
  <div class="modal-background"></div>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Modal title</p>
      <button class="delete" aria-label="close"></button>
    </header>
    <section class="modal-card-body">
      <div class="field">
        <label class="label">Nome do Arquivo</label>
        <div class="control">
          <input class="input" type="text">
        </div>
      </div>
    </section>
    <footer class="modal-card-foot  is-justify-content-flex-end">
      <!-- Quero esses buttons na direita -->
        <div class="buttons">
            <button class="button">Cancel</button>
            <button class="button is-success">Save changes</button>
        </div>
    </footer>
  </div>
</div>
</template>
<script>
export default {
  name: 'Editar',
  props: {
    isActive: {
      type: Boolean,
      default: false
    },
    element: {
      type: Object,
      default: () => ({})  // Valor padrão como um objeto vazio
    }
  }
}
</script>
<style>
.modal-card{
  width: 90%;
}
#columns{
  width: 100%;
  background: red;
}
</style>