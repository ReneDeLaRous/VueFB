<template>
  <div id="app">
    <div id="nav" v-if ="account"> 
      <router-link to="/">Home</router-link> |
     <a @click= "logout">Logout</a>
    </div>
    <div>
      <router-view />
    </div>
     </div>
</template>
<script>
import {accountService} from "@/_services";
export default {
  data(){
    return{
      account:null,
    }
  },
  created(){   //In this method created we call accountService to receive value
    accountService.account.subscribe((x)=>this.account=x);  //it search if somebody logged 
  },
  methods:{
    logout:accountService.logout,
  }
  
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
