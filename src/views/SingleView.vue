<template>
    <div id="page-single">
        <div class="content">
            <div class="img">
                <img :src="`https://robohash.org/${user.id}`"/>
            </div>
            <h2>{{ user.name }}</h2>
        </div>
    </div>
</template>

<script setup> 
    import { onMounted,ref } from 'vue';
    import { useRoute } from "vue-router";
    import axios from 'axios';
    const route = useRoute();
    const loading = ref(true);
    const user = ref({});
    onMounted(async ()=>{
        const id =  route.params.id;
        try {
            let data = await axios.get(`https://jsonplaceholder.typicode.com/users/${id}`);
            user.value = data.data;
        } catch (error) {
            console.log(error);
        }
    })
</script>
<style>
#page-single{
    display: flex;
    flex-direction: column;
    align-items: center;
}
#page-single .content{
    width: 100%;
    padding: 1rem;
    background-color: #fff;
    border-radius: 10px;
}
</style>
