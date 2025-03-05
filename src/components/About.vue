<template>
  <div>
    <h3>Welcome</h3>
    <el-form :model="form" label-width="100px">
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="姓名">
            <el-input v-model="form.name"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="年龄">
            <el-input v-model="form.age"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="8">
          <el-form-item label="地址">
            <el-input v-model="form.address"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
    <h3>动态渲染内容</h3>
      <el-row v-for="(item, index) in form.subObjList" :key="index" :gutter="12" :style="{ background: '#edfced' }">
        <el-col> {{item?.projectNameLabel}}：{{item?.projectName}}</el-col>
        <el-col> {{item?.technicalPointLabel}}：{{item?.technicalPoint}}</el-col>
        <el-col> {{item?.mainFunctionLabel}}：主要功能：{{item?.mainFunction}}</el-col>
        <el-col> {{item?.difficultyLabel}}：{{item?.difficulty}}</el-col>
        <el-col><hr></el-col>
      </el-row>
    </el-form>
    <button @click="setRenderInfo">动态渲染赋值</button>
    <button @click="clearRenderInfo">动态渲染清空</button>
  </div>
</template>

<!--vue3写法-->
<!--<script setup lang="ts" name="About">
import { reactive, ref } from 'vue'
import type { ComponentSize, FormProps } from 'element-plus'

let form = {
  name: '松树戈',
  age: '66',
  address: '这里',
  secondLabel: '我就是第二个标题',
  subObjList: []

}
// 模拟远程请求后对subObjList进行赋值
form.subObjList = [
  { projectNameLabel: '项目名称',
    projectName: 'xx项目前端',
    technicalPointLabel: '技术点',
    technicalPoint: 'vue vuex vue-router js',
    mainFunctionLabel: '主要功能',
    mainFunction: '前端交互ux整改，完善用户体验',
    difficultyLabel: '难点',
    difficulty: '大批量数据渲染'
  },
  { projectNameLabel: '项目名称',
    projectName: 'xx项目后端',
    technicalPointLabel: '技术点',
    technicalPoint: 'springboot mybatis redis pgsql',
    mainFunctionLabel: '主要功能',
    mainFunction: '支持用户的特定业务流程',
    difficultyLabel: '难点',
    difficulty: '大批量数据校验'
  }
]
</script>-->
<!--vue2写法-->
<script>
  export default {
    data() {
      return {
        form: {
          name: '松树戈',
          age: '66',
          address: '这里',
          secondLabel: '我就是第二个标题',
          subObjList: []
        }
      }
    },
    mounted() {
      console.log('在-mounted内部')
    },
    methods: {
      setRenderInfo() {
        this.form.subObjList = [
          { projectNameLabel: '项目名称',
            projectName: 'xx项目前端',
            technicalPointLabel: '技术点',
            technicalPoint: 'vue vuex vue-router js',
            mainFunctionLabel: '主要功能',
            mainFunction: '前端交互ux整改，完善用户体验',
            difficultyLabel: '难点',
            difficulty: '大批量数据渲染'
          },
          { projectNameLabel: '项目名称',
            projectName: 'xx项目后端',
            technicalPointLabel: '技术点',
            technicalPoint: 'springboot mybatis redis pgsql',
            mainFunctionLabel: '主要功能',
            mainFunction: '支持用户的特定业务流程',
            difficultyLabel: '难点',
            difficulty: '大批量数据校验'
          }
        ]
      },
      clearRenderInfo() {
        this.form.subObjList = []
      }
    }
  }
</script>
<style scoped>
.about {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  color: rgb(85, 84, 84);
  font-size: 18px;
}
</style>