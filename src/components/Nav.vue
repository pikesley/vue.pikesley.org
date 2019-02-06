<template>
  <ul id="nav">
    <li v-for="tab in tabs" :key="tab.title">
      <router-link v-bind:to="tab.path">
        {{ tab.title }}
      </router-link>
    </li>
  </ul>
</template>

<script>
import axios from "axios";
var endPoint = "https://data-pikesley.netlify.com/components/nav.json";
export default {
  name: "Nav",
  data() {
    return {
      tabs: []
    };
  },
  mounted() {
    var self = this;
    axios.get(endPoint).then(response => (self.tabs = response.data.data));
  }
};
</script>

<style lang="scss">
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
