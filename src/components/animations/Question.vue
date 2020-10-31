<template>
  <div class=" card">
    <div class="card-header">
    <h2 > {{question}} </h2>
    </div>


      <div class="card-body">
        <form @submit.prevent="checkResult" class="form form-inline">
          <input type="text" placeholder="Resposta:" v-model="reply" class="form-control">
          <button type="submit" class="btn btn-primary">Enviar</button>
        </form>
      </div>

    </div>
</template>

<script>
export default {
      data() {
        return {
          question: "Gerando pergunta...",
          result: 0,
          reply: ''
        }
      },

    created () {
      this.generateQuestion()
    },
    methods: {
      generateQuestion() {
          let numberOne = this.generateRandomNumber(1, 100)
          let numberTwo = this.generateRandomNumber(1, 100)

        this.result = numberOne + numberTwo

        this.question = `Qual é o resultado da soma entre ${numberOne} +  ${numberTwo} ?`
      },

      generateRandomNumber (min, max) {
        return Math.round(Math.random() * (max - min)) + min
      },
      checkResult() {

            let mode = 'answer-error' //default
          if(this.reply == this.result)
                mode = 'answer-success'


            this.$emit('changeMode', mode)

      }
    }
}
</script>

<style scoped>
     .default{
    border: 2px solid blue;
    padding: 10px;
  }
</style>
