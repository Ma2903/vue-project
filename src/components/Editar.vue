<template>
  <div class="EditScreen">
    <h2>Editando: {{ element.nome }}</h2>
    <!-- Renderize o formulário de edição aqui, usando os dados de 'element' -->
    <div>
      <label for="id">ID:</label>
      <input type="text" id="id" v-model="element.id" readonly />

      <label for="nome">Nome:</label>
      <input type="text" id="nome" v-model="element.nome" />

      <label for="payload">Payload:</label>
      <input type="text" id="payload" v-model="element.payload" />

      <label for="tags">Tags:</label>
      <input type="text" id="tags" v-model="element.tags" />

      <label for="tipo">Tipo:</label>
      <input type="text" id="tipo" v-model="element.tipo" />
    </div>
  </div>
</template>
  
  
  <script setup>
  import { defineProps } from 'vue'
  
  const props = defineProps({
    element: {
      type: Object,
      required: true
    }
  })
  </script>
  
<style scoped>
.EditScreen{
  position: absolute;
  top: 0;
  left: 0;
  width: 90%;
  height: 100%;
  margin-left: 5%;
  background: red;
}


</style>
  