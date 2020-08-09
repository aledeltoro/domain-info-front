<template>
  <div>
    <AddDomain v-on:add-domain="addDomain" />

    <HostItem v-if="state == 'ready'" v-bind:host="newHost" />
    <DisclaimerCard v-else-if="state == 'iddle'" />
    <LoadingAnimation v-else />

    <ErrorModal v-bind:error="error" />
  </div>
</template>

<script>
import HostItem from "./HostItem";
import AddDomain from "./AddDomain";
import LoadingAnimation from "./animations/LoadingAnimation";
import DisclaimerCard from "./DisclaimerCard";
import ErrorModal from "./ErrorModal";
import axios from "axios";

export default {
  name: "ShowHost",
  components: {
    HostItem,
    AddDomain,
    DisclaimerCard,
    LoadingAnimation,
    ErrorModal,
  },
  data() {
    return {
      newHost: {},
      state: "iddle",
      error: {
        title: "",
        message: "",
        show: false,
      },
    };
  },
  methods: {
    addDomain(domain) {
      this.state = "";

      axios
        .post(`http://localhost:3000/domains?host=${domain}`)
        .then((res) => {
          this.newHost = res.data;
          this.state = "ready";
        })
        .catch((err) => {
          switch (err.response.status) {
            case 400:
              this.error.title = "Client Error";
              this.error.message = err.response.data;
              break;
            case 408:
              this.error.title = "Timeout Error";
              this.error.message = err.response.data;
              break;
            case 500:
              this.error.title = "Server Error";
              this.error.message =
                "Something went wrong during the search. Try again later.";
              break;
            default:
              this.error.title = "Unknown Error";
              this.error.message = "Try again later.";
              break;
          }

          this.error.show = true;
          this.state = "iddle";
        });
    },
  },
};
</script>

<style scoped>
</style>