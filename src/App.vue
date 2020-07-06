<template>
  <div id="app">
    <div id="nav">
        <manage-admin>
            <router-view/>
        </manage-admin>
      <!--<router-link to="/">Home</router-link> |-->
      <!--<router-link to="/about">About</router-link>-->
    </div>
  </div>
</template>
<script>
    import manageAdmin from './components/Manage'
    export default {
        name:'App',
        components:{
            manageAdmin
        }
    }
</script>
<style lang="scss">
html,body,#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 0px;
    padding: 0px;
    width: 100%;
    height: 100%;
}

#nav {
    height:100%;
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
