<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1 class="text-left text-info"> Awesome Quiz</h1>
      </div>
    </div>
    <hr>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <component :is="componentCon" @answered = "answered($event)" ></component>
      </div>
    </div>
  </div>
</template>
<script>
import answer from "./component/Answer.vue"
import question from "./component/Question.vue"
export default {
  components:{
    appQuestion:question,
    appAnswer:answer
  },
  data:()=>{
    return{
      componentCon:'app-question'
    }
  },
  methods:{
    answered(isCorrect){

      if(isCorrect =='true'){
        this.componentCon ='app-answer'
      }
      else{
        this.componentCon='app-question';
        alert("wrong Answer")
        window.location.reload();

      }
    }
  }

}
</script>
<style lang="scss" scoped>

</style>
