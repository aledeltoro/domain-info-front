<template>
  <b-container>
    <b-form @submit="addDomain" v-if="show">
      <b-form-group
        id="input-group-1"
        label-for="input-1"
        label-align-md="left"
        description="e.g., google.com, twitter.com"
      >
        <b-form-input
          id="input-1"
          v-model="form.domain"
          type="text"
          required
          placeholder="Enter domain name"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </b-container>
</template>

<script>
export default {
  name: "AddDomain",
  data() {
    return {
      form: {
        domain: ""
      },
      show: true
    };
  },
  methods: {
    addDomain(e) {
      e.preventDefault();
      this.$emit("add-domain", this.form.domain);
      this.form.domain = "";
    }
  }
};
</script>

<style lang="scss" scoped>
</style>