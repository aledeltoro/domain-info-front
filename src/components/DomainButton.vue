<template>
  <div class="list-bottom">
    <b-button
      :pressed="false"
      variant="success"
      size="lg"
      @click="$emit('get-domains')"
    >List Domains</b-button>
  </div>
</template>

<script>
export default {
  name: "DomainButton"
};
</script>

<style>
.list-bottom {
  margin: 10px;
}
</style>