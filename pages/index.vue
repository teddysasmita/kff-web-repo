<template>
<el-row :gutter=20 type="flex">
  <el-col :span="8" :offset=6>
    <h1 class="companyname">KFF-Web</h1>
    <h2 class="main">Selamat Datang</h2>
    <el-form ref="form" :model="loginform">
      <el-form-item label="Nama User"><el-input v-model="loginform.username"></el-input></el-form-item>
      <el-form-item label="Password"><el-input v-model="loginform.password" type="password"></el-input></el-form-item>
      <el-form-item><el-button type="primary" @click="checkuser">Login</el-button></el-form-item>
    </el-form>
  </el-col>
</el-row>
</template>

<script>
// import axios from 'axios'

export default {
  data: function () {
    return {
      loginform: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    checkuser: function () {
      // function to verify user and password
      console.log('checkuser')
    }
  }
}
</script>

<style>
body {
  /*margin-top: 100px;*/
  text-align: center;
}

.main {
  text-align: center;
}

.companyname {
  text-align: center;
  color: blue;
}
</style>
