<template>
  <b-modal
    ref="error-modal"
    size="sm"
    v-bind:title="error.title"
    ok-only
    ok-variant="info"
  >
	{{ error.message }}
	</b-modal>
</template>

<script>
export default {
  name: "ErrorModal",
  props: ["error"],
  methods: {
    showModal() {
      this.$refs["error-modal"].show();
    },
    hideModal() {
      this.$refs["error-modal"].hide();
    }
  },
  updated() {
    this.showModal();
  }
};
</script>

<style coped>
</style>