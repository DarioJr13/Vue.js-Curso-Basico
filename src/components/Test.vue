<template>
<div>
<h1>Hello Engenieer Dario {{ title }} {{ user.lastName }}</h1>
<div v-if="showName">
<p>{{user.firstName}}</p>
</div>
<div v-else>
<p>No se ha asignado ningún Nombre</p>
</div>
<hr>
<ul>
<li v-for="task in tasks">
{{ task.title}}
</li>
</ul>
<input type="text" v-model="user.firstName">
<button type="button" v-on:click="saludar(user.firstName)">
CLICK ME
</button>
<input type="text" v-on:keyup.enter="typedEnter">
<div class="test">
<!--{{user.firstName + ' ' + user.lastName}}-->
<!--{{ fullName }}-->
{{ msg }}
</div>
</div>
</template>

<script>
export default{
data(){
return {
  title: 'Hola Vuejs',
  user: {
    firstName: 'Joe',
    lastName: 'McMillan'
  },
  myHtml: '<h3>Html</h3>',
  showName: false,
  tasks: [
    {title: 'eat'},
    {title:'dinner'},
    {title:'play'},
    {title:'taks'}
  ]
}
},
methods: {
saludar(name) {
  alert( 'hello' + name)
},
typedEnter (e) {
 // console.log(e.target.value);
 //console.log('Acciono un Enter');
}
},
computed: {
  fullName() {
    return this.user.firstName + ' ' + this.user.lastName;
}
},
props: {
  msg: {
    type: String,
    default: 'Mensaje por Defecto'
  }
}
}
</script>


<style media="screen">
.test{
background-color: #eee ;
}
</style>
