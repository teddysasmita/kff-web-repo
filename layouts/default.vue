<template>
  <div>
    <el-row class="myheader" gutter="8px" type="flex">
      <el-col class="mytitle" :span="12">KING FRESH FROZEN Administration System</el-col>
      <el-col class='myuser' :span="8">User: {{ this.user.username }}</el-col>
      <el-col class='mybutton' v-if="this.user.username !== 'Silakan login'" :span='4'>
        <el-button @click="logout" size="mini" type="danger">Keluar</el-button></el-col>
    </el-row>
    <nuxt/>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      user: {
        username: 'Silakan login'
      }
    }
  },
  created: function () {
    var temp = this.$ls.get('user', 'Silakan login')
    if (temp === 'Silakan login') {
      this.user = { username: 'Silakan login' }
      this.$router.push('/')
    } else {
      this.user = temp
    }
  },
  methods: {
    logout: function () {
      this.$ls.clear()
      this.user = { username: 'Silakan login' }
      this.$router.push('/')
    }
  }
}
</script>

<style>
.myheader {
  margin: 8px;
  vertical-align: middle;
}

.mytitle {
  padding: 5px;
  background-color: rgba(203, 197, 49, 0.7);
  text-align: center;

}

.myuser {
  padding: 5px;
  text-align: center;
  background-color: #33c46f
}

.mybutton {
  padding: 5px;
}
</style>
