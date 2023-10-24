<template>
    <div>
            <div v-if='isAut'>
               <div> Приветствую вас {{userName}}</div>
            <button @click="logout">ВЫЙТИ</button>
</div>

    <div v-else>
        <label>Введите ваше имя:</label>
        <input v-model='userName'/>
        <button @click="login">Войти</button>
    </div>
</div>
    </template>



<script>
export default{
    name: 'HomePage',
data(){
    return{
        isAut: false,
        userName:''
    }
},
methods:{
    login(){
        if(this.UserName !== ''){
            this.isAut = true
            localStorage.setItem('isAuth', true)
            localStorage.setItem('userName',this.userName)
        } else{
            alert('Введите логин')
        }
    },
    logout(){
        this.isAut = false
        this.userName = ''
        localStorage.removeItem('isAuth')
        localStorage.removeItem('userName')
    }
  },
  created() {
    if(localStorage.getItem('isAuth')) {
        this.isAut = true
        this.userName = localStorage.getItem('userName')
    }

  }
}
</script>