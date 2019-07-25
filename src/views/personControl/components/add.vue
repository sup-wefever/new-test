<template>
  <el-form :model="form" label-width="100px">
    <el-form-item label="名称">
      <el-input v-model="form.date"/>
    </el-form-item>
    <el-form-item label="活动区域">
      <el-input v-model="form.name"/>
    </el-form-item>
    <el-form-item label="活动形式">
      <el-input v-model="form.province"/>
    </el-form-item>
    <el-form-item label="活动形式">
      <el-input v-model="form.city"/>
    </el-form-item>
    <el-form-item label="活动形式">
      <el-input v-model="form.address"/>
    </el-form-item>
    <el-form-item label="活动形式">
      <el-input v-model="form.zip"/>
    </el-form-item>
    <el-form-item label="名称">
      <el-button type="danger" @click="submit">确认</el-button>
      <el-button type="info" @click="cancel">取消</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  props: ['item'],
  data() {
    return {
      form: {
        date: '',
        name: '',
        province: '',
        city: '',
        address: '',
        zip: ''
      }
    }
  },
  created() {
    this.initForm()
  },
  methods: {
    initForm() {
      this.item !== 'add' && (this.form = this.item)
    },
    submit() {
      this.$emit('confirm', this.form)
    },
    cancel() {
      this.$emit('cancel')
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
