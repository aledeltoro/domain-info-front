<template>
  <div class="list-button">
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
.list-button {
  margin: 10px;
}
</style>