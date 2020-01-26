<template>
  <div>
    <el-card>
      <data-bar :amount="amount" :panel-group-title="panelGroupTitle" />
    </el-card>
    <el-card style="margin-top: 30px">
      <task-button />
    </el-card>
    <el-card style="margin-top: 30px">
      <task-collapse />
    </el-card>
  </div>
</template>

<script>
import DataBar from './components/DataBar'
import TaskButton from './components/TaskButton'
import TaskCollapse from './components/TaskCollapse'
export default {
  name: 'Index',
  components: { TaskCollapse, TaskButton, DataBar },
  data() {
    return {
      amount: [10, 5, 6, 24],
      panelGroupTitle: ['待完成任务', '已完成任务', '待完成目标', '已用时间']
    }
  }
}
</script>

<style scoped>

</style>
