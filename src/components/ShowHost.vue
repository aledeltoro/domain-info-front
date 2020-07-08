<template>
  <div>
    <AddDomain v-on:add-domain="addDomain" />
    <HostItem v-if="state == 'ready'" v-bind:host="newHost" />
    <DisclaimerCard v-else-if="state == 'iddle'" />
    <LoadingAnimation v-else/>
  </div>
</template>

<script>
import HostItem from "./HostItem";
import AddDomain from "./AddDomain";
import LoadingAnimation from "./animations/LoadingAnimation";
import DisclaimerCard from "./DisclaimerCard";
import axios from "axios";

export default {
  name: "ShowHost",
  components: {
    HostItem,
    AddDomain,
    DisclaimerCard,
    LoadingAnimation
  },
  data() {
    return {
      newHost: {},
      state: "iddle"
    };
  },
  methods: {
    addDomain(domain) {
      this.state = "";

      axios
        .post(`http://localhost:3000/domains?host=${domain}`)
        .then(res => {
          this.newHost = res.data;
          this.state = "ready";
          console.log(res.status);
        })
        .catch(() => {
          alert("Error ocurred");
          this.state = "iddle";
        });
    }
  }
};
</script>

<style scoped>
</style>