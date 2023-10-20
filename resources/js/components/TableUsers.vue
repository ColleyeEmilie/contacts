<script setup>
defineProps({
    data: Array
});
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
        <a>
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
