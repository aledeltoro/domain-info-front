<template>
  <b-navbar type="dark" variant="primary">
    <b-navbar-brand>Domain Info</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-navbar-nav justified="true">
      <b-nav-item to="/">Home</b-nav-item>
      <b-nav-item @click="getDomains" to="/domains">Domains</b-nav-item>
    </b-navbar-nav>
  </b-navbar>
</template>

<script>
export default {
  name: "Header",
  methods: {
    getDomains() {
      this.$emit("list-domains");
    }
  }
};
</script>

<style>
#nav a.router-link-exact-active {
  color: #ffffff;
}
</style>