<template>
  <el-dialog
    style="text-align: left;width: 80%"
    title="添加普通番茄钟"
    :visible.sync="dialogPomodoroTaskVisible"
  >
    <el-form>
      <el-form-item label="PomodoroName">
        <el-input v-model.trim="pomodoro.name" />
      </el-form-item>
      <!--      <el-form-item label="TaskTag"><br>-->
      <!--        &lt;!&ndash;        <el-input v-model.trim="task.tag" />&ndash;&gt;-->
      <!--        <el-radio-group v-model.trim="task.tag">-->
      <!--          <el-radio label="普通番茄钟" />-->
      <!--          <el-radio label="定目标" />-->
      <!--        </el-radio-group>-->
      <!--      </el-form-item>-->
      <el-form-item label="PomodoroEndDate">
        <!--        <el-input v-model.trim="task.endDate" />-->
        <el-date-picker v-model.trim="pomodoro.endDate" type="date" placeholder="截止日期" style="width: 100%;" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submit">Submit</el-button>
      </el-form-item></el-form>
  </el-dialog>
</template>

<script>
export default {
  name: 'NewPomodoroTask',
  props: {
    pomodoro: {
      type: Object,
      default: () => {
        return {
          name: '',
          tag: 'pomodoro',
          endDate: ''
        }
      }
    },
    visible: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    dialogPomodoroTaskVisible: {
      get() {
        return this.visible
      },
      set(val) {
        this.$emit('update:visible', val)
      }
    }
  },
  methods: {
    submit() {
      this.dialogTaskVisible = false
      this.$message({
        message: 'Task information has been submit successfully',
        type: 'success',
        duration: 5 * 1000
      })
      console.log(this.task.tag)
    }
  }
}
</script>

<style scoped>

</style>
