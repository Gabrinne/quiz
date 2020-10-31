<template>
  <div class="container">
    <h2 v-text="title"></h2>
  <!--   <app-question @changeMode="changeMode"></app-question> -->

    <div class="row">
      <div class="col">
        <transition name="effect" mode="out-in">
      <component :is="mode" @changeMode="changeMode">
      </component >

    </transition>
      </div>
    </div>

    </div>
</template>

<script>

import Question from "./Question"
import AnswerSuccess from "./AnswerSuccess"
import AnswerError from "./AnswerError"

export default {
      data() {
        return {
          title: "Quiz",
          mode: 'app-question'
        }
      },

      components: {
        'app-question': Question,
        'answer-success': AnswerSuccess,
        'answer-error': AnswerError
      },

       methods: {
           changeMode(mode) {
             if( mode == undefined)
                  this.mode = 'app-question'
            else
                this.mode = mode
        }
  }
}
</script>

<style scoped>

  /* SAÍDA */
  .effect-leave-active {
    animation: effect-out 2.5s;
  }

  /* entrada */
  .effect-enter-active {
    animation: effect-in 2.5s;
  }

      /* SAÍDA */
    @keyframes effect-out {
        to {
          transform: rotateY(90deg)
        }

        from {
          transform: rotateY(0deg)
        }
    }
    /* entrada */
    @keyframes effect-in {
        to {
          transform: rotateY(0deg)
        }

        from {
          transform: rotateY(90deg)
        }
    }
</style>
