<template>
  <div>
    <b-row align-content="center">
      <b-col>
        <b-card
          align="left"
          :header="domain.domainName"
          :img-src="domain.hostInfo.logo"
          img-height="auto"
          img-top
          tag="domain"
          style="max-width: 18rem;"
          class="mb-2"
        >
          <b-card-body>{{domain.hostInfo.title}}</b-card-body>

          <b-list-group flush>
            <b-list-group-item>
              <strong>SERVERS CHANGED:</strong>
              {{domain.hostInfo.servers_changed}}
            </b-list-group-item>

            <b-list-group-item>
              <strong>SSL GRADE:</strong>
              {{domain.hostInfo.ssl_grade}}
            </b-list-group-item>

            <b-list-group-item>
              <strong>PREVIOUS SSL GRADE:</strong>
              {{domain.hostInfo.previous_ssl_grade}}
            </b-list-group-item>

            <b-list-group-item>
              <strong>DOMAIN DOWN:</strong>
              {{domain.hostInfo.is_down}}
            </b-list-group-item>
          </b-list-group>
        </b-card>
      </b-col>
      <b-col>
        <b-table striped hover :items="getServerDetails"></b-table>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "DomainItem",
  props: ["domain"],
  data() {
    return {
      servers: []
    };
  },
  computed: {
    getServerDetails() {
      let servers = [];

      this.domain.hostInfo.servers.forEach(server => {
        servers.push(server);
      });
      console.log(servers);
      return this.domain.hostInfo.servers;
    }
  }
};
</script>

<style lang="scss" scoped>
</style>