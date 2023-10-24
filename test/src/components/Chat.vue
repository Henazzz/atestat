<template>
    <div v-if="userName">
        <div class="chat">
            <h2>Чат</h2>
            <div class="text" v-for="message in messages" :key="message.id">
{{ message.user }}: {{ message.text }}
            </div>

<div class="empty" v-show="emptyMsg">Сообщений нет</div>
</div>

<input v-model="newMessage"/>
<button @click="sendMessage">Отправить</button>
<button @click="delMessage">Удалить</button>

        </div>
    <div v-else>
        Для авторизации перейдите по <router-link :to="{name:'Home'}">ссылке</router-link>

    </div>
    </template>


<script>


export default{
    name: 'ChatComp',
    data(){
        return{
            messages:[],
            newMessage:'',
            emptyMsg:true,
            userName: localStorage.getItem('userName')
        }
    },
    methods: {
        sendMessage(){
            if(this.newMessage !==''){
                this.emptyMsg = false
                this.messages.push({id: new Date().getTime(), text: this.newMessage, user: this.userName})
                this.saveChatRecords.apply()
                this.newMessage=''
                console.log(this.messages);
 
            }
        },
        delMessage(){
this.messages=[]
localStorage.removeItem('messages_${this.userName}', JSON.stringify(this.messages))
this.emptyMsg = true
        },
        saveChatRecords(){
            const records = this.messages
            localStorage.setItem('messages_${this.userName}',JSON.stringify(records))
        },
        LoadChatRecords(){
            const records = JSON.parse(localStorage.getItem('messages_${this.userName}'))
       if(records){
        this.emptyMsg = false,
        this.messages = records
       }
     }
  } , 
  created(){
    this.LoadChatRecords()
  }
}
</script>
<style>
.chat {
  margin-top: 20px;
}

.text {
  margin-bottom: 10px;
  padding: 5px;
  border: 1px solid #ccc;
}

.empty {
  margin-top: 10px;
  color: #999;
}

input {
  margin-top: 10px;
  padding: 5px;
  width: 200px;
}

button {
  margin-top: 10px;
  padding: 5px 10px;
  background-color: #42b983;
  color: white;
  border: 0;
  cursor: pointer;
}
</style>