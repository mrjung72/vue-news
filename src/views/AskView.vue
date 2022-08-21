<template>
  <div>
    <div v-for="ask in asks">
        <div>{{ ask.title }} ... {{ ask.time_ago }}</div>
    </div>
  </div>
</template>

<script>
import { fetchAskList } from '../api/index.js';

export default {
    data() {
        return {
            asks: []
        }
    },
    created() {

        fetchAskList() 
            .then(Response => this.asks = Response.data)
            .catch()
    }

}
</script>
