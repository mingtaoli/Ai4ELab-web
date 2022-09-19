<script lang="ts" setup>
import axios from "axios";
async function callpropremote() {
  try {
    const res = await axios.post("http://127.0.0.1:8000/api/coolprop", {
      //不考虑proxy和跨域的话，这个例子能够返回结果
      params: {
        x: x.value,
        y: y.value,
      },
    });
    //const res = await axios.get('api/hello');
    console.log(res);

    remoteanswer.value = res.data;
  } catch (err) {
    alert(err);
  }
}
</script>
<template>
  <h1>CoolProp is here</h1>
  <br />
  <el-select v-model="value" class="m-2" placeholder="Select">
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.label"
      :value="item.value"
    />
  </el-select>
  <br />
  <el-select v-model="value" class="m-2" placeholder="Select">
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.label"
      :value="item.value"
    />
  </el-select>
  <br />
  <el-select v-model="value" class="m-2" placeholder="Select" size="small">
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.label"
      :value="item.value"
    />
  </el-select>
  <br />
  <el-button @click="callpropremote">submit </el-button>
</template>
