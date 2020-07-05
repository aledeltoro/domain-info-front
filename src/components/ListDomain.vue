<template>
  <div class="list-items">
    <DomainButtom v-on:get-domains="getDomains" />
    <div v-bind:key="domain.id" v-for="domain in domains">
      <DomainItem v-bind:domain="domain" />
    </div>
  </div>
</template>

<script>
import DomainItem from "./DomainItem";
import DomainButtom from "./DomainButton";
import axios from "axios";

export default {
  name: "ListDomain",
  components: {
    DomainItem,
    DomainButtom
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
          alert(err);
        });
    }
  }
};
</script>

<style>
.list-items {
  margin: 50px;
}
</style>