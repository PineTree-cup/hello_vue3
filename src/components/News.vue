<template>
  <div class="new-tabs">
    <el-tabs
        v-model="editableTabsValue"
        type="card"
        class="demo-tabs"
        editable
        @edit="handleTabsEdit"
    >
      <template #add-icon>
        <el-icon><Select/></el-icon>
      </template>
      <el-tab-pane
          v-for="item in editableTabs"
          :key="item.name"
          :label="item.title"
          :name="item.name"
      >
        {{ item.content }}
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script setup lang="ts" name="News">
import axios from "axios";
import { ref } from 'vue'
import { Select } from '@element-plus/icons-vue'
import type { TabPaneName } from 'element-plus'
let tabIndex = 2
const editableTabsValue = ref('2')
const editableTabs = ref([
  {
    title: 'Tab 1',
    name: '1',
    content: 'Tab 1 news content',
  },
  {
    title: 'Tab 2',
    name: '2',
    content: 'Tab 2 news content',
  },
])

const handleTabsEdit = (
    targetName: TabPaneName | undefined,
    action: 'remove' | 'add'
) => {
  if (action === 'add') {
    const newTabName = `${++tabIndex}`
    editableTabs.value.push({
      title: 'New Tab',
      name: newTabName,
      content: 'New Tab content',
    })
    editableTabsValue.value = newTabName
  } else if (action === 'remove') {
    const tabs = editableTabs.value
    let activeName = editableTabsValue.value
    if (activeName === targetName) {
      tabs.forEach((tab, index) => {
        if (tab.name === targetName) {
          const nextTab = tabs[index + 1] || tabs[index - 1]
          if (nextTab) {
            activeName = nextTab.name
          }
        }
      })
    }

    editableTabsValue.value = activeName
    editableTabs.value = tabs.filter((tab) => tab.name !== targetName)
  }
}
function getNews() {
  axios.get('http://localhost:8888/list').then(
      response => {
        console.log('response', response)
      },
      error => {
        console.log('error', error)
      }
  )
}

</script>

<style scoped>
/* 新闻 */
.new-tabs :deep(.el-tabs__new-tab){
  height: 30px;
  width: 30px;
  border-radius: 15px;
  font-size: 16px;
}
.news {
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  height: 100%;
}

.news ul {
  margin-top: 30px;
  list-style: none;
  padding-left: 10px;
}

.news li > a {
  font-size: 18px;
  line-height: 40px;
  text-decoration: none;
  color: #64967E;
  text-shadow: 0 0 1px rgb(0, 84, 0);
}

.news-content {
  width: 70%;
  height: 90%;
  border: 1px solid;
  margin-top: 20px;
  border-radius: 10px;
}
</style>