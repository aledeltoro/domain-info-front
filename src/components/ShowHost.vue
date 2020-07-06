<template>
  <div>
    <AddDomain v-on:add-domain="addDomain" />
    <HostItem v-bind:host="newHost" />
  </div>
</template>

<script>
import HostItem from "./HostItem";
import AddDomain from "./AddDomain";
import axios from "axios";

export default {
  name: "ShowHost",
  components: {
    HostItem,
    AddDomain
  },
  data() {
    return {
      newHost: {}
    };
  },
  methods: {
    addDomain(domain) {
      axios
        .post(`http://localhost:3000/domains?host=${domain}`)
        .then(res => {
          this.newHost = res.data;
          console.log(res.status);
        })
        .catch(err => {
          if (err.response) {
            alert(err.response.data);
          }
        });
    }
  }
};
</script>

<style lang="scss" scoped>
</style>