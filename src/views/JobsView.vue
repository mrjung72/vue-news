<template>
  <div>
    <div v-for="job in jobs">
        <div>{{ job.title }} ... {{ job.time_ago }}</div>
    </div>
  </div>
</template>

<script>
import { fetchJobsList } from '../api/index.js';

export default {
    data() {
        return {
            jobs: []
        }
    },
    created() {

        fetchJobsList() 
            .then(Response => this.jobs = Response.data)
            .catch()
    }

}
</script>

<style>

</style>