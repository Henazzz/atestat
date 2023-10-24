<template>
    <div>
        <nav>
<RouterLink to='/'>Домашняя страница</RouterLink>
<RouterLink to='/chat'>Чат</RouterLink>
<RouterLink to='/test'>Подгрузка API данных</RouterLink>
        </nav>
    </div>
</template>


<script>
export default{
    name:'NavComp'
}</script>
<style>
nav {
  background-color: #f2f2f2;
  padding: 10px;
  display: flex;
  justify-content: space-evenly;
  width: 3000px;
}

nav a {
  text-decoration: none;
  color: #333;
  padding: 5px;
}

nav a:hover {
  background-color: #e8e8e8;
}
</style>