<template>
    <el-dialog :visible="visible" :title="title" @close="close" width="800px" :append-to-body="true">
        <vcrontab @hide="visible=false"  :expression="expression"
                  @fill="crontabFill"
        ></vcrontab>
    </el-dialog>
</template>
<script>
import vcrontab from "@/components/cron";
export default {
    props:{
        value:{
            type:String,
            default: ''
        },

    },
    model: {
        prop: 'value',
        event: 'change',
    },
    components:{
        vcrontab
    },
    name:'cronDialog',
    data(){
        return {
            expression:'',
            visible:false,
            title:'cron表达式'
        }
    },
    methods:{
        crontabFill(value){
            this.$emit('change', value)
        },
        open(){
            this.visible=true
            this.expression=this.value
        },
        close(){
            this.visible=false
        }
    }
}
</script>
