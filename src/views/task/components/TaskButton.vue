<template>
  <el-row style="text-align: center">
    <el-col :span="10" :offset="1">
      <el-card shadow="hover">
        <el-row>普通番茄钟</el-row>
        <el-row>
          <i class="el-icon-circle-plus-outline" @click="clickPomodoroTaskDialog" />
        </el-row>
      </el-card>
    </el-col>
    <el-col :span="10" :offset="2">
      <el-card shadow="hover">
        <el-row>定目标</el-row>
        <el-row>
          <i class="el-icon-circle-plus-outline" @click="clickTargetTaskDialog" />
        </el-row>
      </el-card>
    </el-col>
    <new-pomodoro-task :visible.sync="showPomodoroTaskDialog" />
    <new-target-task :visible.sync="showTargetTaskDialog" />
  </el-row>
</template>

<script>
import NewPomodoroTask from './NewPomodoroTask'
import NewTargetTask from './NewTargetTask'
export default {
  name: 'TaskButton',
  components: { NewTargetTask, NewPomodoroTask },
  data() {
    return {
      showPomodoroTaskDialog: false,
      showTargetTaskDialog: false
    }
  },
  methods: {
    clickPomodoroTaskDialog() {
      this.showPomodoroTaskDialog = true
    },
    clickTargetTaskDialog() {
      this.showTargetTaskDialog = true
    }
  }
}
</script>

<style scoped>
.el-button{
  width: 100px;
}
  .el-row{
    line-height: 30px;
    color: #666;
  }
  .el-icon-circle-plus-outline{
    font-size: 30px;
    color: #666;
  }
</style>
