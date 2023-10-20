<script setup>
import {ref} from "vue";

defineProps({
    data: Array,
    showModal: Boolean,
});

function openModal(id){
    const data = ref();
     axios.get('/api/users/'+ id).then(function (response) {
       data.value = response.data;
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
</template>
