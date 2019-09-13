<template>
  <div class="alert alert-success text-center" >
    <h3>correct Answer</h3>
    <hr>
    <button class="btn btn-success" @click= "nxtQ">Next</button>
  </div>
</template>
<script>
export default {
  methods:{
    nxtQ(){
      this.$emit('confirmed')
    }
  }
}
</script>
<style lang="scss" scoped>

</style>
