<template>
  <div class="alert alert-danger ">
    {{title}}

      <p>Erro na resposta!</p>

      <button @click="nextQuestion" class="btn btn-danger">
          próxima pergunta
      </button>

    </div>
</template>

<script>
export default {
    data() {
      return {
        title: 'Erro!'
      }
    },

    methods: {
      nextQuestion() {
        this.$emit('changeMode')
      }
    }
}
</script>

<style scoped>
  .error{
    border: 2px solid red;
    padding: 10px;
  }
</style>
