<template>
<div class="app">
  <NavComp></NavComp>
  <router-view></router-view>
</div>
</template>

<script>
import NavComp from './components/Navigation.vue'


export default {
  name: 'App',
  components: {
    NavComp
  
  }
}
</script>

<style>
.app {
display: flex;
flex-direction: column;
align-items: center;
height: 100%;
font-family: Arial, sans-serif;
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 10px
}


.NavComp {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #333;
  color: #fff;
  /* padding: 10px; */
  border-radius: 5px
}

.NavComp a {
  color: #fff;
  text-decoration: none;
  margin-right: 10px;
}

.router-view {
  margin-top: 20px;
}

</style>
