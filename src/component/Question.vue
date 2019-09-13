<template>

  <div class="panel panel-default">
    <div class="panel-heading">
      <div class="panel-title">
        {{question}}
      </div>
    </div>
    <div class="panel-body">
      <div class="col-sx-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg" style="margin:10px;"  @click="onSub(btndata[0].correct)">{{btndata[0].a}}</button>
        <button class="btn btn-primary btn-lg" style="margin:10px;"  @click="onSub(btndata[1].correct)">{{btndata[1].a}}</button>
        <hr>
        <button class="btn btn-primary btn-lg" style="margin:10px;"  @click="onSub(btndata[2].correct)">{{btndata[2].a}}</button>
        <button class="btn btn-primary btn-lg" style="margin:10px;"  @click="onSub(btndata[3].correct)">{{btndata[3].a}}</button>
      </div>




    </div>


  </div>

</template>
<script>


export default {


  data(){
    return{

        question:'hello',
        btndata:[
          {correct:true,a:0},
          {correct:false,a:0},
          {correct:false,a:0},
          {correct:false,a:0},
        ]

    }
  },
  methods:{
    ran: function (min, max) {
			let r = Math.max(Math.floor(Math.random() * max) + 1, min);
			return r;
    },
    gqustion(){
      let questionPattern = Math.floor(Math.random() * (1 + 1));
      let n1 = this.ran(1,100);
      let n2  = this.ran(0,100);
      let ans;

      if(questionPattern ==0){
        ans = (n1+n2)
      }else{
        ans = (n1-n2)
      }

      switch(questionPattern){
        case 0:
          this.question = `What is ${n1} + ${n2} ?`;
          break;

        case 1:
          this.question = `What is ${n1} - ${n2} ?`;
          break;

        default:
          this.question = `Some error accured`

      }
      let slctcrtbtn = Math.floor(Math.random() * (3 + 1));
      this.btndata[0].a = this.ran(ans-this.ran(5,20),ans+this.ran(5,20));
      this.btndata[0].correct='false';
      this.btndata[1].a = this.ran(ans-this.ran(5,20),ans+this.ran(5,20));
      this.btndata[1].correct='false';
      this.btndata[2].a = this.ran(ans-this.ran(5,20),ans+this.ran(5,20));
      this.btndata[2].correct='false';
      this.btndata[3].a = this.ran(ans-this.ran(5,20),ans+this.ran(5,20));
      this.btndata[3].correct='false';
      this.btndata[slctcrtbtn].correct='true'
      this.btndata[slctcrtbtn].a = ans;
    },
    onSub(isCorrect){

      this.$emit('answered',isCorrect)
    }


    },
     mounted:function(){
      this.gqustion();
  }

}
</script>
<style lang="scss" scoped>

</style>
