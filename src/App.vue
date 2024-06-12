<script setup>
import { ref, onMounted } from 'vue'
import Element from './components/Element.vue'
import Editar from './components/Editar.vue'

// Definindo a variável reativa para armazenar o estado do botão
const awesome = ref(false)
// Definindo a variável reativa para armazenar os dados do banco
const elements = ref([])
// Variável reativa para armazenar o elemento selecionado para edição
const selectedElement = ref(null)

// Função para alternar o estado da variável 'awesome' e armazenar o elemento clicado
const Switch = (element) => {
  awesome.value = !awesome.value
  selectedElement.value = element
}

// Função assíncrona para carregar os componentes a partir do banco
async function loadComponents() {
  // Supondo que API.read() seja uma chamada para a API que retorna os dados
  const response = await API.read()
  elements.value = response.data // Atribuindo a resposta à variável 'elements'
}

// Chamando a função loadComponents quando o componente é montado
onMounted(() => {
  loadComponents()
})
</script>

<template>
  <div>
    <header class=""> 
      <h1> Objetos de Aprendizagem </h1>
      <section class="search"> 
        <input type="text" placeholder="Digite Algo..."> 
        <i class='bx bx-search-alt'></i>
      </section>
      <section class="buttons">
        <button class="all"> TUDO </button>
        <button class="text"> TEXTO </button>
        <button class="audio"> ÁUDIO </button>
        <button class="picture"> IMAGENS </button>
      </section>
    </header>
    <main>
      <section class="content">
        <!-- Iterando sobre o array 'elements' e renderizando o componente 'Element' para cada item -->
        <Element 
          v-for="(element, index) in elements" 
          :key="index" 
          :nome="element.nome" 
          @click="() => Switch(element)"
        />
        <!-- Renderizando o componente 'Editar' com base no estado de 'awesome' e passando o elemento selecionado -->
        <Editar v-if="awesome" :element="selectedElement" />
      </section>
    </main>
  </div>
</template>


<style scoped>
.element{
  height: 300px;
  width: 100%;
  border-radius: 15%;
  display: flex;
  position: relative;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  border: 3px solid #000;
  overflow: hidden;
}
.img{
  width: 90%;
  height: 90%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
.description{
  width: 100%;
  height: 30%;
  background-color: #5265f7;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 0 0 30px 30px;
}
</style>