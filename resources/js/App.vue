<script setup>
import {ref} from "vue";
import TableUsers from "./components/TableUsers.vue";
const showModal = ref(false);

const data = ref([]);
    axios.get('/api/users').then(function (response) {
         data.value = response.data.data;
    });
</script>

<template>
    <TableUsers :data=data />
    <button @click="showModal = true">Show Modal</button>
    <div v-show="showModal">
        <p> Test </p>
        <button  @click="showModal = false">OK</button>
    </div>
</template>

