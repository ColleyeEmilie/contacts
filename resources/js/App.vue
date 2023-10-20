<script setup>
import {ref} from "vue";
import TableUsers from "./components/TableUsers.vue";

const data = ref([]);
    axios.get('/api/users').then(function (response) {
         data.value = response.data.data;
    });
</script>

<template>
    <TableUsers :data=data />
</template>

