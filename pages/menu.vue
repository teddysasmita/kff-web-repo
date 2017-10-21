<template>
<el-row type="flex" :gutter="10">
<el-col :span="6">
  <el-row><el-col><h2>Sistem</h2></el-col></el-row>
  <el-row><el-col><el-button type="text" @click="clickuser">Administrasi Pengguna</el-button></el-col></el-row>
</el-col>
</el-row>

</template>

<script>
export default {
  methods: {
    clickuser: function () {
      this.$router.push('/users')
    }
  }
}
</script>
