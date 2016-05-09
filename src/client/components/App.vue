<template>
  <div
    v-cloak
    v-if="monitors !== null && version !== null">
    <List></List>
    <Output></Output>

    <footer>
      <p>
        <a href="https://github.com/typicode/hotel">
          <i class="fa fa-building-o"></i>
          <span>{{version}}</span>
          <span>README</span>
        </a>
      </p>
    </footer>
  </div>
</template>

<script>
import List from './List.vue'
import Output from './Output.vue'
import * as actions from '../actions'

export default {
  components: { List, Output },
  vuex: {
    getters: {
      monitors: (state) => state.monitor,
      version: (state) => state.version
    },
    actions
  },
  created() {
    this.watchMonitors()
    this.fetchVersion()
  },

}
</script>
