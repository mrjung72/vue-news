<template>
  <div class="content">
    <div v-for="user in users">
        <div>{{ user.user }}</div>
    </div>

  </div>
</template>

<script>
import { fetchNewsList } from '../api/index.js';

export default {
  name: "modal_message",
  props: {
    msg: String,
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
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
