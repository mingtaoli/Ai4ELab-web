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
  
  const answer = ref(0);
  const remoteanswer = ref(1);
function getAnswer() {

    answer.value++

}

function getAnswerremote() {
  const res=  axios.get('/api/addxy', {
    params: {
            x: 2,
            y: 3
          }
        });

 //这块怎么写？搞不定了，julia端显示已经请求成功，这边无法搞出来
}





  </script>
<template>
    <el-row class="mb-4">
      <el-button @click="getAnswer">本地计算测试</el-button>

      <el-button type="primary">{{answer}}</el-button>

      <el-button @click="getAnswerremote">远程计算测试</el-button>

      <el-button type="primary">{{remoteanswer}}</el-button>

    </el-row>
  
    <el-row class="mb-4">
      <el-button plain>Plain</el-button>
      <el-button type="primary" plain>Primary</el-button>
      <el-button type="success" plain>Success</el-button>
      <el-button type="info" plain>Info</el-button>
      <el-button type="warning" plain>Warning</el-button>
      <el-button type="danger" plain>Danger</el-button>
    </el-row>
 
  </template>
  
