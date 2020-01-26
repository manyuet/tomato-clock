<template>
  <el-dialog
    style="text-align: left;width: 80%"
    title="添加目标"
    :visible.sync="dialogTargetTaskVisible"
  >
    <el-form>
      <el-form-item label="TargetName">
        <el-input v-model.trim="target.name" />
      </el-form-item>
      <el-form-item label="TargetEndDate">
        <el-date-picker v-model.trim="target.endDate" type="date" placeholder="截止日期" style="width: 100%;" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submit">Submit</el-button>
      </el-form-item></el-form>
  </el-dialog>
</template>

<script>
export default {
  name: 'NewTargetTask',
  props: {
    target: {
      type: Object,
      default: () => {
        return {
          name: '',
          tag: 'target',
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
    dialogTargetTaskVisible: {
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
      this.dialogTargetTaskVisible = false
      this.$message({
        message: 'Task information has been submit successfully',
        type: 'success',
        duration: 5 * 1000
      })
    }
  }
}
</script>

<style scoped>

</style>
