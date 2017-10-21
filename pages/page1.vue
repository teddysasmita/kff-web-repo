<template>
  <div class="page1">
    <el-row>
      <el-col :span="6"><h1>{{ msg }}</h1></el-col>
      <el-col :span="6"><el-button type='success'>Press this</el-button></el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  // layout: 'form',
  data: function () {
    return {
      msg: 'This is the first page'
    }
  }
}
</script>

<style>
.page1 {
  margin-top: 50px;
  margin-left: 50px;
}

</style>
