<template>
  <section class="element">
    <section class="img"> 
      Imagem de um Livro
      <section class="del"> </section>
    </section>
    <section class="description"> {{ nome }} </section>
  </section>
</template>

<script>
export default {
  props: {
    nome: {
      type: String,
      required: true
    }
  }
};
</script>

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