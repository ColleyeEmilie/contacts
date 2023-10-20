<script setup>
import {ref, reactive} from "vue";

const showModal = ref(false);
const data = ref([]);
const dataAll = ref([]);
const dataLinks = ref([]);
const dataUser = ref({});
axios.get('/api/users').then(function (response) {
    dataAll.value = response.data.data;
});
axios.get('/api/users').then(function (response) {
    data.value = response.data.data;
});
axios.get('/api/users').then(function (response) {
    dataLinks.value = response.data.links;
});
function getPages(label){
    axios.get('/api/users/?page=' + label)
        .then(function (response) {
            dataLinks.value = response.data.links;
            console.log(dataLinks.value[label]);
        });
}

function openModal(id) {
    showModal.value = true;
    axios.get('/api/users/' + id)
        .then(function (response) {
        dataUser.value = response.data;
    });
}
</script>

<template>
    <table>
        <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Birthday</th>
        </tr>
        <tr v-for="user in data">
            <td>
                <a @click="openModal(user.id)">
                    {{ user.name }}
                </a>
            </td>
            <td>
                {{ user.email }}
            </td>
            <td>
                {{ user.born_at }}
            </td>
        </tr>
    </table>
    <div v-show="showModal">
        <p> Nom : {{ dataUser.name }} </p>
        <p> Email : {{ dataUser.email }} </p>
        <p> Date de naissance : {{ dataUser.born_at }} </p>
        <button @click="showModal = false">OK</button>
    </div>


    <div class="pagination">
        <a v-for="link in dataLinks" @click="getPages(link.label)"><p class="pagination__text">{{ link.label }}</p></a>
    </div>
</template>

