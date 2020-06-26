<template>
  <div class="home">
    <AddDomain v-on:add-domain="addDomain" />
  </div>
</template>

<script>
import AddDomain from "../components/AddDomain";
import axios from "axios";

export default {
  name: "Home",
  components: {
    AddDomain
  },
  methods: {
    addDomain(domain) {
      axios
        .post(`http://localhost:3000/domains?host=${domain}`)
        .then(res => {
          console.log(res.data);
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>
