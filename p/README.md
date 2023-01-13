

# vue-crontab-f
![img.png](img.png)
vue 的 cron 组件，支持解析/反解析 cron 表达式，生成最近五次的符合条件时间，依赖 vue2 和 element-ui
修复vue-crontab的一些问题
- 小时选择范围0-23
- 可自己输入cron表达式(有些特殊符号,自己输入方便)
- 验证cron表达式规则(cron-parser)
- 解析cron表达式(cronstrue)

## 安装方式

```
npm install vcrontab
```

## 引入方式

```javascript
//全局引入
import vcrontab from "vcrontab2";
Vue.use(vcrontab); //使用方式：<vcrontab></vcrontab>

//单独引入
import vcrontab from "vcrontab2";
export default {
  components: { vcrontab },
};
```

## 代码示例

```javascript
<template>
    <div id="app">
        <div class="box">
            <el-input v-model="input" placeholder class="inp"></el-input>
            <el-button type="primary" @click="showDialog">生成 cron</el-button>
        </div>
        <el-dialog title="生成 cron" :visible.sync="showCron">
            <vcrontab @hide="showCron=false" @fill="crontabFill" :expression="expression"></vcrontab>
        </el-dialog>
    </div>
</template>

<script>
import vcrontab from 'vcrontab2'
export default {
    components: { vcrontab },
    data() {
        return {
            input: "",
            expression: "",
            showCron: false
        };
    },
    methods: {
        crontabFill(value) {
            //确定后回传的值
            this.input = value;
        },
        showDialog() {
            this.expression = this.input;//传入的 cron 表达式，可以反解析到 UI 上
            this.showCron = true;
        }
    }
};
</script>
```

## 参数

- expression
  传入的 cron 表达式，可以反解析到 UI 上

- hideComponent
  需要隐藏的组件数组，依次为`['second','min','hour','day','month','week','year']`

## 方法

- fill
  点击确定时，把选择好的值返回。

- hide
  关闭组件时的回调
## 参考
* https://zh.wikipedia.org/wiki/Cron
* https://onefeng.xyz/wiki/cron/
