<template>
  <div>
    <div v-bind:key="domain.id" v-for="domain in domains">
      <DomainItem v-bind:domain="domain" />
    </div>
  </div>
</template>

<script>
import DomainItem from "./DomainItem";

export default {
  name: "DomainList",
  components: {
    DomainItem
  },
  props: ["domains"]
};
</script>

<style lang="scss" scoped>
</style>