<template>
  <div class="list-items">
    <DomainButtom v-on:get-domains="getDomains" />
    <div v-bind:key="domain.id" v-for="domain in domains">
      <DomainItem v-bind:domain="domain" />
    </div>

    <ErrorModal v-bind:error="error" />
  </div>
</template>

<script>
import DomainItem from "./DomainItem";
import DomainButtom from "./DomainButton";
import ErrorModal from "./ErrorModal";
import axios from "axios";

export default {
  name: "ListDomain",
  components: {
    DomainItem,
    DomainButtom,
    ErrorModal,
  },
  data() {
    return {
      domains: [],
      error: {
        title: "",
        message: "",
        show: false,
      },
    };
  },
  methods: {
    getDomains() {
      axios
        .get("http://localhost:3000/domains")
        .then((res) => {
          res.data.items.forEach((item) => {
            this.domains.push(item);
          });
        })
        .catch((err) => {
          switch (err.response.status) {
            case 500:
              this.error.title = "Server Error";
              this.error.message =
                "Something went wrong during the fetch. Try again later.";
              break;
            default:
              this.error.title = "Unknown Error";
              this.error.message = "Try again later.";
              break;
          }

          this.error.show = true;
        });
    },
  },
};
</script>

<style>
.list-items {
  margin: 50px;
}
</style>