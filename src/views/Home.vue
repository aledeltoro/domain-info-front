<template>
  <div class="home">
    <AddDomain v-on:add-domain="addDomain" />
    <HostItem v-bind:host="newHost" />
  </div>
</template>

<script>
import AddDomain from "../components/AddDomain";
import HostItem from "../components/HostItem";
import axios from "axios";

export default {
  name: "Home",
  components: {
    AddDomain,
    HostItem
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
