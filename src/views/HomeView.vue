<template>
  <div id="page-home">
    <div class="items">
      <RouterLink :to="{ name: 'discover', params: { id: user.id }}" class="card" v-for="(user,index) in users" :key="index">
        <div class="img">
          <img :src="`https://robohash.org/${user.id}`"  alt="">
        </div>

        <div class="content">
          <p>nom: {{ user.name }}</p>
        </div>
      </RouterLink>
    </div>
  </div>
</template>
<script setup>
  import { onMounted,ref } from 'vue';
  import axios from 'axios';
  const users = ref([]);
  const loading = ref(true);
  onMounted(async () => {
    try {
      let data = await axios.get('https://jsonplaceholder.typicode.com/users');
      users.value = data.data;
    } catch (error) {
      console.log(`fetch error`);
    }
  })
</script>
  
<style>
 #page-home .items{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
 }
 #page-home .items .card{
  width: 30%;
  height: 200px;
  background-color: #fff;
  box-shadow: -2px 3px 30px -10px rgba(0,0,0,0.37);
  border-radius: 10px;
  margin-bottom: 10px;
  transition: all 300ms ease-in;
}
#page-home .items .card .img{
  width: 100%;
  height: 120px;
}
#page-home .items .card .img img{
  width: 100%;
  height: 100%;
}
#page-home .items .card .content{
  padding: 5px;
}
</style>
