<template>
  <div>
    <DomainButton v-on:get-domains="getDomains" />
    <DomainList v-bind:domains="domains" />
  </div>
</template>

<script>
import DomainList from "../components/DomainList";
import DomainButton from "../components/DomainButton";
import axios from "axios";

export default {
  name: "Domain",
  components: {
    DomainList,
    DomainButton
  },
  data() {
    return {
      domains: []
    };
  },
  methods: {
    getDomains() {
      axios
        .get("http://localhost:3000/domains")
        .then(res => {
          res.data.items.forEach(item => {
            this.domains.push(item);
          });
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>

<style lang="scss" scoped>
</style>