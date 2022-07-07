<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" :clipped="clipped" fixed app>
      <v-list>
        <v-list-item v-for="(route, i) in routes" :key="i" :to="route.to" router exact>
          <v-list-item-action>
            <v-icon>{{ route.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="route.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
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