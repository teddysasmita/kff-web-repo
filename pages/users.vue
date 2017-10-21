<template>
<div class="users">
<el-row :gutter=15  type="flex" justify="center">
  <el-col :span="4">
    <el-table ref="userstable"  :data="userslist" highlight-current-row @current-change="selectuser">
      <el-table-column label="Nama User" prop="username"></el-table-column>
    </el-table>
    <el-button class="btnappend" type="warning" @click="appenduser">Tambah</el-button>
  </el-col>
  <el-col :span="16">
    <h3>{{ detiltitle }}</h3>
    <el-tabs v-model="maintab" type="border-card" @tab-click="tabclick">
      <el-tab-pane label="Detil" name="detil">
        <el-form label-width="120px" :model="user">
          <el-form-item label="Nama Login"><el-input v-model="user.username"></el-input></el-form-item>
          <el-form-item label="Alamat"><el-input v-model="user.address"></el-input></el-form-item>
          <el-form-item label="No Kontak"><el-input v-model="user.phone"></el-input></el-form-item>
          <el-form-item label="Password"><el-input v-model="user.password" type="password"></el-input>
          </el-form-item>
          <el-form-item label="Konfirmasi"><el-input v-model="passwordconfirm" type="password"></el-input>
          </el-form-item>
          <el-form-item label="Nama Lengkap"><el-input v-model="user.fullname"></el-input></el-form-item>
          <el-form-item label="Tempat Lahir"><el-input v-model="user.pob"></el-input></el-form-item>
          <el-form-item label="Tanggal Lahir"><el-date-picker v-model="user.dob" format="yyyy/MM/dd"></el-date-picker></el-form-item>
          <el-form-item label="Kota"><el-input v-model="user.city"></el-input></el-form-item>
          <el-form-item label="E-mail"><el-input v-model="user.email"></el-input></el-form-item>
          <el-form-item>
            <el-button type="primary" @click="postuser">Simpan</el-button>
            <el-button type="danger" @click="deleteuser">Hapus</el-button>
          </el-form-item>
        </el-form>
      </el-tab-pane>
      <el-tab-pane label="Otoritas" name="otoritas">
        <el-row :gutter="15"  type="flex" justify="center">
          <el-col :span="8">
            <el-table ref="userauthstable" :data="userauthslist" highlight-current-row @current-change="selectuserauth">
              <el-table-column label="Otoritas User" prop="item_name"></el-table-column>
              <el-table-column label="Operasi">
                <template scope="scope">
                  <el-button size="small" type="danger" @click="deleterole">Hapus</el-button>
                </template>
              </el-table-column>
            </el-table>
          </el-col>
          <el-col :span="8">
            <el-table ref="authstable" :data="authslist" highlight-current-row @current-change="selectauth">
              <el-table-column label="Otoritas" prop="name"></el-table-column>
              <el-table-column label="Operasi">
                <template scope="scope">
                  <el-button size="small" type="success" @click="addrole">Tambah</el-button>
                </template>
              </el-table-column>
            </el-table>
          </el-col>
        </el-row>
      </el-tab-pane>
    </el-tabs>
  </el-col>
</el-row>
</div>
</template>

<script>
// import axios from 'axios'

export default {
  layout: 'form',
  created: function () {
    this.getusers()
  },
  data: function () {
    return {
      userslist: [],
      user: {
        id: '',
        username: '',
        fullname: '',
        pob: '',
        dob: '',
        phone: '',
        address: '',
        city: '',
        email: '',
        password: '',
        active: '',
        accessToken: '',
        authKey: '',
        userlog: '',
        datetimelog: ''
      },
      availrole: {
        name: '',
        type: 1,
        description: '',
        rule_name: '',
        data: '',
        created_at: '',
        updated_at: ''
      },
      userrole: {
        item_name: '',
        user_id: '',
        created_at: ''
      },
      passwordconfirm: '',
      detiltitle: 'Data Baru',
      mode: 'insert',
      userauthslist: [],
      authslist: [],
      maintab: 'detil'
    }
  },
  methods: {
    tabclick: function (clickedtab) {
      if (this.maintab === 'otoritas') {
        this.getauths()
        this.getuserauths()
      }
    },
    addrole: function () {
      this.userrole.item_name = this.availrole.name
      this.userrole.user_id = this.user.id
      this.userrole.created_at = ''
      // function to add role. Connect to server
    },
    deleterole: function () {
      // function to delete role. Connect to server
    },
    getusers: function () {
      // function to get users list. Connect to server
    },
    getuserauths: function () {
      // function to get user's authorizations list. Connect to server
    },
    getauths: function () {
      // function to get authorizations list. Connect to server
    },
    selectuserauth: function (val) {
      if (val !== null) {
        if (val !== null) {
          for (var p in this.userrole) {
            this.userrole[p] = val[p]
          }
        }
      }
    },
    selectauth: function (val) {
      if (val !== null) {
        for (var p in this.availrole) {
          this.availrole[p] = val[p]
        }
      }
    },
    selectuser: function (val) {
      if (val !== null) {
        for (var p in this.user) {
          this.user[p] = val[p]
        }
        if (this.maintab === 'otoritas') {
          this.getauths()
          this.getuserauths()
        }
        this.user.password = ''
        this.passwordconfirm = ''
        this.detiltitle = this.user.username
        this.mode = 'update'
      }
    },
    appenduser: function () {
      this.user = {
        id: '',
        username: '',
        fullname: '',
        pob: '',
        dob: '',
        phone: '',
        address: '',
        city: '',
        email: '',
        password: '',
        active: '',
        accessToken: '',
        authKey: '',
        userlog: '',
        datetimelog: ''
      }
      this.mode = 'insert'
    },
    postuser: function () {
      // function to post any modification user data. Connect to server
    },
    deleteuser: function () {
      // function to delete user. connect to server
    }
  }
}
</script>

<style>
.users { margin: 20px };
.btnappend { margin: 20px};
.btnauth { margin: 10px };
</style>
