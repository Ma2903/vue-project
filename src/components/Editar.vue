<template>
    <div>
      <h2>Editando: {{ element.nome }}</h2>
      <!-- Renderize o formulário de edição aqui, usando os dados de 'element' -->
      <div>
        <p>ID: {{ element.id }}</p>
        <p>Nome: {{ element.nome }}</p>
        <p>Payload: {{ element.payload }}</p>
        <p>Tags: {{ element.tags }}</p>
        <p>Tipo: {{ element.tipo }}</p>
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
  
  