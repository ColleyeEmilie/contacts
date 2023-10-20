<script setup>
    import {ref} from "vue";
    const data = ref([]);

    axios.get('/api/users').then(function (response) {
         data.value = response.data.data;
    });
</script>

<template>
    <table>
        <tr v-for="user in data">
            <td>
                <a>
                    {{ user.name }}
                </a>
            </td>
        </tr>
    </table>

</template>

<style scoped>
</style>
