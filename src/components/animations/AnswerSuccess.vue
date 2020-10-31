<template>
  <div class="alert alert-success">
    {{title}}

      <p>Sucesso na resposta!</p>
      <button @click="nextQuestion" class="btn btn-success">
          próxima pergunta
      </button>
    </div>
</template>

<script>
export default {
    data() {
      return {
        title: 'Sucesso!'
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

     .success{
    border: 2px solid green;
    padding: 10px;
  }

</style>
