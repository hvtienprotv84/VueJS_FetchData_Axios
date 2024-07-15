<template>
<h1 style="text-align: center;">Fetch Data và Fetch Data Axios</h1>
<hr/>
  <div class="container">
     <h1 style="text-align: center; margin-top: -10px;">Fetch Data</h1>
    <br>
    <br>
<table class="table table-bordered" style="margin-top: -50px;">
  <thead class="table-success">
    <tr>
      <th scope="col">ID</th>
      <th scope="col">Name</th>
      <th scope="col">Email</th>
      <th scope="col">Gender</th>
      <th scope="col">Status</th>
    </tr> 
  </thead>
  <tbody>
    <tr v-for="listData in getListData" :key="listData.id">
      <th >{{ listData.id }}</th>
      <th >{{ listData.name }}</th>
      <th >{{ listData.email }}</th>
      <th >{{ listData.gender }}</th>
      <th >{{ listData.status }}</th>
    </tr>
  </tbody>
</table>
<br>
<h1 class="text-center" style="margin-top: -20px;">Fetch Data with Axios</h1>
<br>
<table class="table table-bordered text-center">
  <thead class="table-success">
    <tr>
      <th scope="col">ID</th>
      <th scope="col">Email</th>
      <th scope="col">First Name</th>
      <th scope="col">Last Name</th>
      <th scope="col">Avatar</th>
    </tr> 
  </thead>
  <tbody>
    <tr v-for="(info, index) in users" :key="index">
      <td v-text="info.id"></td>
      <td v-text="info.email "></td>
      <td v-text="info.first_name"></td>
      <td v-text="info.last_name" ></td>
      <td ><img :src="info.avatar" alt="" width="30" height="30" class="rounded-circle"></td>
    </tr>
  </tbody>
</table>
  </div>
</template>
<script>
import  axios  from 'axios';
export default {
  name: 'App',
  data() {
    return {
      getListData: [],
      users: []
    }
  },
  methods: {
      fetchData(){
        axios.get('https://gorest.co.in/public/v2/users?page=1&per_page=10').then((res) => {
          this.getListData = res.data;
        });      
      },
      getUser(){
        const url = 'https://reqres.in/api/users?page=2';
         axios
         .get(url)
         .then(rest => {
          this.users = rest.data.data
         })
      }
    },
    mounted(){
    this.fetchData();
    this.getUser();
  },
}
</script>
<style scoped>
 .create {
  margin-right: 90%;
 }
</style>
