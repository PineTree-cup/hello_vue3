<template>
  <h1>首页</h1>
  <el-tabs v-model="activeName" class="demo-tabs" @tab-click="handleClick">
    <el-tab-pane label="User" name="first">User</el-tab-pane>
    <el-tab-pane label="Config" name="second">Config</el-tab-pane>
    <el-tab-pane label="Role" name="third">Role</el-tab-pane>
    <el-tab-pane label="Task" name="fourth">Task</el-tab-pane>
<!--    我做了一些修改-->
  </el-tabs>
</template>

<script setup lang="ts" name="Home">

import {ref} from "vue";

const activeName = ref('first')
import type { TabsPaneContext } from 'element-plus'
</script>

<style scoped>
  .home {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }
</style>