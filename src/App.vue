<template>
<div>
  <h2>Daftar Murid Program Unggulan</h2>
   <table  style="width:30%">
  <tr>
    <th>No</th>
    <th>Nama</th>
    <th>Alamat</th>
  </tr>
  <tr v-for="user in users" :key="user.id">
    <td>{{ user.id }}</td>
    <td>{{ user.name }}</td>
    <td>{{ user.alamat }}</td>
  </tr>
</table>
</div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return{
      users: []
    }
  },
  mounted() {
    this.load()
  },
  methods: {
    load() {
      axios.get('http://localhost:3000/users').then(res =>{
        this.users = res.data
      }).catch((err) => {
        console.log(err);
      })
    }
  }
}
</script>
<style>
table, th, td {
  border:1px solid black;
  border-radius: 10px;
  text-align: center;
}
table{
  background-color: lightskyblue;
}
th{
  background-color: lime;
}
td{
  background-color: white;
}
</style>