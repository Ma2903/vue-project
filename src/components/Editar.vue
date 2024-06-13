<template>
  <div class="container is-max-widescreen is-large has-background-white">
    <h2>Editando: {{ element.nome }}</h2>
    <!-- Renderize o formulário de edição aqui, usando os dados de 'element' -->
      <div class="field">
        <label class="label">Nome</label>
        <div class="control">
          <input class="input" v-model="element.nome">
        </div>
      </div>

      <!-- <div class="file is-info has-name is-medium">
        <label class="file-label">
          <input class="file-input" type="file" name="resume" />
          <span class="file-cta">
            <span class="file-icon">
              <i class="fas fa-upload"></i>
            </span>
            <span class="file-label"> Info file… </span>
          </span>
          <span class="file-name"> Screen Shot 2017-07-29 at 15.54.25.png </span>
        </label>
      </div> -->

      <div class="field">
        <label class="label">Tags</label>
        <div class="control">
          <input class="input" v-model="element.tags">
        </div>
      </div>
      <div class="field">
        <label class="label">Tipo</label>
        <div class="control">
          <input class="input" v-model="element.tipo">
        </div>
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
.container{
  top: 0;
  left: 10%;
  position: absolute;
  height: 100vh;
  width: 80%;
  background: red;
}


</style>
  
