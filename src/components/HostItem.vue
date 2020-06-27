<template>
  <b-container class="host-item">
    <b-row align-content="center">
      <b-col sm="4">
        <b-card
          align="left"
          :header="host.title"
          :img-src="host.logo"
          img-height="25%"
          img-top
          tag="domain"
          style="max-width: 18rem;"
          class="mb-2"
        >
          <b-list-group flush>
            <b-list-group-item>
              <strong>SERVERS CHANGED:</strong>
              {{host.servers_changed}}
            </b-list-group-item>

            <b-list-group-item>
              <strong>SSL GRADE:</strong>
              {{host.ssl_grade}}
            </b-list-group-item>

            <b-list-group-item>
              <strong>PREVIOUS SSL GRADE:</strong>
              {{host.previous_ssl_grade}}
            </b-list-group-item>

            <b-list-group-item>
              <strong>DOMAIN DOWN:</strong>
              {{host.is_down}}
            </b-list-group-item>
          </b-list-group>
        </b-card>
      </b-col>
      <b-col>
        <b-table striped hover :items="host.servers"></b-table>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "HostItem",
  props: ["host"]
};
</script>

<style scoped>
.host-item {
  margin: 20px auto;
}
</style>