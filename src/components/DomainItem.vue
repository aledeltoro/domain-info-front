<template>
  <div>
    <p>{{domain.domainName}}</p>
  </div>
</template>

<script>
export default {
  name: "DomainItem",
  props: ["domain"]
};
</script>

<style lang="scss" scoped>
</style>