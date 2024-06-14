
<template>
  <div class="cell">
    <div class="card">
    <div class="card-image"> 
      <figure class="image is-3by2">
        <img src="https://bulma.io/assets/images/placeholders/96x96.png">
      </figure>
    </div>
    <div class="card-content">
      <div class="content is-flex is-justify-content-space-between is-align-items-center">
        <span>{{ nome }}</span> 
        <div class="buttons">
          <button class="button is-danger has-text-white">
            <span class="icon is-small">
              <i class='bx bxs-trash'></i>
            </span>
          </button>
          <button class="button is-link has-text-white" @click="activateEdit">
            <span class="icon is-small">
              <i class='bx bxs-edit'></i>
            </span>
          </button>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  props: {
    nome: {
      type: String,
      required: true
    }
  },
  name: 'Element',
  methods: {
    activateEdit() {
      this.$emit('activate-edit');
    }
  }
};
</script>

<style scoped>

</style>