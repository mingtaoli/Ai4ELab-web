<script lang="ts" setup>
import { ref } from 'vue';
import {
  Check,
  Delete,
  Edit,
  Message,
  Search,
  Star,
} from '@element-plus/icons-vue';
import { controlledComputed } from '@vueuse/shared';
import axios from 'axios';

const x = ref(3);
const y = ref(6);

const answer = ref(0);
const remoteanswer = ref("string");
function getAnswer() {

  answer.value=x.value+y.value

}

async function getAnswerremote() {

  try {
    const res = await axios.get('http://127.0.0.1:8000/api/addxy', {
        //不考虑proxy和跨域的话，这个例子能够返回结果
      params: {
        x: x.value,
        y: y.value
      }
    });
    //const res = await axios.get('api/hello');
    console.log(res);
    
    remoteanswer.value = res.data;
  } catch (err) {
    alert(err)
  }
}



</script>
<template>
  <el-row class="mb-4">
    <el-input v-bind:value="x" placeholder="Please input x" />
    <el-input v-bind:value="y" placeholder="Please input y" />
    <!-- 怎么写个框框输入数字，还要查， -->
    <el-button @click="getAnswer">本地计算测试</el-button>

    <el-button type="primary">{{answer}}</el-button>

    <el-button @click="getAnswerremote">远程计算测试</el-button>

    

    <el-button type="primary">{{remoteanswer}}</el-button>

  </el-row>


</template>
  
