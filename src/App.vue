<script setup>
import { ref, onMounted } from 'vue'
import Element from './components/Element.vue'
import Editar from './components/Editar.vue'

// Definindo a variável reativa para armazenar o estado do botão
const awesome = ref(false)
// Definindo a variável reativa para armazenar os dados do banco
const elements = ref([])
// Variável reativa para armazenar o elemento selecionado para edição
let selectedElement = ref(null)

// Função para alternar o estado da variável 'awesome' e armazenar o elemento clicado
const Switch = (element) => {
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
  <div class="p-5">
    <h1 class="title is-3"> Objetos de Aprendizagem </h1>
    <div class="columns">
      <section class="column mr-4 is-three-quarters"> 
        <div class="field has-addons">
          <div class="control is-expanded">
            <input class="input w-full" type="text" placeholder="Find a repository">
          </div>
          <div class="control">
            <button class="button is-link">
              <i class='bx bx-search-alt-2 is-size-4'></i>
            </button>
          </div>
        </div>
      </section>
      <div class="column field is-grouped ml-5">
          <p class="control">
            <button class="button is-link"> Todos </button>
          </p>
          <p class="control">
            <button class="button is-link is-outlined"> Texto </button>
          </p>
          <p class="control">
            <button class="button is-link is-outlined"> Audio </button>
          </p>
          <p class="control">
            <button class="button is-link is-outlined"> Imagem </button>
          </p>
      </div>
    </div>
    <main class="fixed-grid has-4-cols">
      <div class="grid is-gap-6">
        <!-- Iterando sobre o array 'elements' e renderizando o componente 'Element' para cada item -->
        <Element 
          v-for="(element, index) in elements" 
          :key="index" 
          :nome="element.nome"
          @activate-edit="handleActivateEdit"
        />
        <!-- Renderizando o componente 'Editar' com base no estado de 'awesome' e passando o elemento selecionado -->
      </div>
</main>
</div>
<Editar :element="selectedElement" :isActive="isActive" id="editScreen"/>
</template>

<script>
  export default {
    name: 'App',
    components: {
      Element,
      Editar
    },
    data() {
      return {
        isActive: false,
        element: null  // Inicialmente null, ou você pode definir um objeto vazio se necessário
      };
    },
    methods: {
      handleActivateEdit() {
        this.isActive = true;
        this.element = element;  // Defina um valor apropriado para `element`
      }
    }
  }
</script>
<style scoped>
/* .element{
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
} */
</style>
