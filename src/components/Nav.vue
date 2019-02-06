<template>
  <nav class="row">
    <div class="three columns" id="brand">
      <router-link v-bind:to="'/'">
        pikesley.org
      </router-link>
    </div>
    <div class="nine columns" id="nav-menu">
      <ul>
        <li v-for="tab in tabs" :key="tab.title">
          <router-link v-bind:to="tab.path">
            {{ tab.title }}
          </router-link>
        </li>
      </ul>
    </div>
  </nav>
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
