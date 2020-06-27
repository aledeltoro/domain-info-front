<template>
  <div class="home">
    <AddDomain v-on:add-domain="addDomain" />
    <DomainItem v-bind:domain="newDomain" />
  </div>
</template>

<script>
import AddDomain from "../components/AddDomain";
import DomainItem from "../components/DomainItem";
import axios from "axios";

export default {
  name: "Home",
  components: {
    AddDomain,
    DomainItem
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
          console.log(res.data);
        })
        .catch(err => {
          alert(err);
        });
    }
  }
};
</script>
