<template>
  <v-app dark>
    <v-app-bar fixed elevate-on-scroll app>
      <v-row justify="center">
        <v-col>
          <v-spacer />
        </v-col>

        <v-col>
          <v-tabs centered background-color="#272727">
            <v-tab :to="routes[0].to" router exact>
              {{ routes[0].title }}
            </v-tab>
          </v-tabs>
        </v-col>

        <v-col cols="1">
          <v-img id="logo" src="..\LOGO.svg" />
        </v-col>

        <v-col>
          <v-tabs centered background-color="#272727">
            <v-tab :to="routes[1].to" router exact>
              {{ routes[1].title }}
            </v-tab>
          </v-tabs>
        </v-col>

        <v-col>
          <v-spacer />
        </v-col>
      </v-row>
    </v-app-bar>
    <v-main>
      <v-container fluid>
        <Nuxt />
      </v-container>
    </v-main>

    <v-footer fixed app>
      <span>Tourangeau GYM Club &copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>

export default {
  name: 'DefaultLayout',
  data() {
    return {
      routes: [
        {
          title: "L'association",
          to: '/home'
        },
        {
          title: 'Les rendez-vous',
          to: '/agenda'
        }
      ],
    }
  }
}
</script>

<style scoped>
.v-tab:hover::before {
  opacity: 0 !important;
}

#logo {
  z-index: 9999!important;
  position: fixed !important;
}
</style>
