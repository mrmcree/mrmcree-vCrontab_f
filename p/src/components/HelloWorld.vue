<template>
  <div class="hello">
      <el-input v-model="cronExpression" @click.native="$refs.cronDialog.open()" style="width: 200px" placeholder="clickHere"></el-input>
      <cronDialog ref="cronDialog" v-model="cronExpression"></cronDialog>
  </div>
</template>

<script>
import cronDialog from "./cronDialog";
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
    data(){
      return{
          cronExpression:'',
      }
    },
    components:{
        cronDialog
    },
    methods:{
        crontabFill(val){

        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
