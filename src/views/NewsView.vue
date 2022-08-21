<template>
  <div>
    <div v-for="user in users">
        <div>{{ user.title }} ... {{ user.time_ago }}</div>
    </div>

    <ModalView v-if="isModalViewed" @close-modal="isModalViewed = false">
        <Contents msg="Hello Vue in CodeSandbox!" />
    </ModalView>
    <button @click="isModalViewed = true">Open Modal</button>

  </div>
</template>

<script>
import ModalView from "../components/ModalView.vue";
import Contents from "../components/Content.vue";
import { fetchNewsList } from '../api/index.js';

export default {
  components: {
    Contents,
    ModalView,
  },
    data() {
        return {
            users: [],
            isModalViewed: false
        }
    },
    created() {

        fetchNewsList() 
            .then(Response => this.users = Response.data)
            .catch()
    }

}
</script>

<style>

</style>