<template>
  <v-app dark>
    <v-app-bar fixed app>
      <v-spacer />
      <v-row justify="center">
        <v-col>
          <v-tabs centered grow background-color="#272727">
            <v-tab v-for="(route, i) in routes" :key="i" :to="route.to" router exact>
              {{ route.title }}
            </v-tab>
          </v-tabs>
        </v-col>
      </v-row>
      <v-spacer />
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
import { mdiHome, mdiCalendar } from '@mdi/js'

export default {
  name: 'DefaultLayout',
  data() {
    return {
      icons: [mdiHome, mdiCalendar],
      clipped: false,
      drawer: false,
      routes: [
        {
          icon: 'mdi-home',
          title: 'Accueil',
          to: '/home'
        },
        {
          icon: 'mdi-calendar',
          title: 'Agenda',
          to: '/agenda'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: ["L'association", "Les rendez-vous"]
    }
  }
}
</script>

<style scoped>
.v-tab:hover::before {
      opacity: 0!important;
}
</style>