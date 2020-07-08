<template>
  <b-container align-h="center" class="disclaimer-card">
    <b-card border-variant="danger">
      <b-card-title title>
        <b-icon-exclamation-circle-fill /> <strong>Disclaimer</strong>
      </b-card-title>
      <b-card-text class="text">This operation may take up to 2 minutes to be processed.</b-card-text>
      <b-card-text class="text">Otherwise, it will be timed out, you may try again once more.</b-card-text>
    </b-card>
  </b-container>
</template>

<script>
export default {
  name: "DisclaimerCard"
};
</script>

<style scoped>
.disclaimer-card {
  width: 40%;
  margin-top: 20px;
}

.text {
  line-height: 30%;
}
</style>