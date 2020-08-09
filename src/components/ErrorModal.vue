<template>
  <b-modal
    ref="error-modal"
    size="sm"
    v-bind:title="error.title"
    ok-only
    ok-variant="info"
    v-model="error.show"
  >{{ error.message }}</b-modal>
</template>

<script>
export default {
  name: "ErrorModal",
  props: ["error"],
};
</script>