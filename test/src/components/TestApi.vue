<template>
<div>
    <div>КОМАНДЫ</div>
    <div v-if="isLoad">Загрузка данных...</div>
    <div v-else>
        <div v-for="(el, i) in teamData" :key="el.id">
            {{ i + 1 }}. {{ el.abbreviation }} {{ el.city }}
        </div>
    </div>
</div>

</template>


<script>
export default{
    name:'TestApi',
    data(){
        return{
            teamData: [],
            isLoad: true
        }
    },
    mounted(){
        const fetch = require('node-fetch');

const url = 'https://free-nba.p.rapidapi.com/teams?page=0';
const options = {
  method: 'GET',
  headers: {
    'X-RapidAPI-Key': 'c141ef7be5msh3c7d4812b7e40e6p1e9804jsn38ecb95d097b',
    'X-RapidAPI-Host': 'free-nba.p.rapidapi.com'
  }
};
fetch(url,options). 
then(res=>res.json())
.then(res=> {
    this.teamData = res.data
    this.isLoad = false
})
    }
}
</script>

