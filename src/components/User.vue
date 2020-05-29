<template>
<div class="users">
<h1>User Component</h1>
<ul>
<li v-for="user in users">
{{user.name}} - {{user.email}} <button v-on:click="deleteUser(user)">X</button>
</li>
</ul>

<form v-on:submit.prevent="addUser">
<input type="text" v-model="newUser.name" placeholder="Name" >
<input type="email" v-model="newUser.email" placeholder="Email" >
 <button type="submit">
 Add
 </button>
</form>
</div>
</template>

<script>
export default {
data(){
  return {
    users: [
      {
        name: 'Joe',
        email:'joe@mail.com',
        contacted: false
         },
         {
        name: 'Ryan',
        email:'ryan@mail.com',
        contacted: false
         },
         {
        name: 'Donna',
        email:'donna@mail.com',
        contacted: true
         }
    ],
    newUser: {}
  }
},
methods: {
  addUser(){
    this.users.push(this.newUser);
    this.newUser = {};
    //console.log('Agregando Usuario', this.newUser);
  },
  deleteUser(user){
    this.users.splice(this.users.indexOf(user), 1);

  },
  created(){
   //console.log('Componente Creado');
  this.$http.get('https://jsonplaceholder.typicode.com/users')
   .then(res => this.users = res.body);
  }
}
}
</script>

<style lang="css">
.users{
background: #333;
color: #fff;
padding: 20px;
}
</style>
