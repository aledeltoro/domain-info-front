<template>
  <b-container fluid="true">
    <b-navbar toggleable="sm" type="light" variant="light" fixed="bottom">
      <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>

      <b-navbar-brand>Domain Info</b-navbar-brand>

      <b-collapse id="nav-text-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-text>Created by Alejandro del Toro</b-nav-text>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </b-container>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style>
</style>