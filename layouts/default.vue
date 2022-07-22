<template>
  <v-app dark>
    <v-app-bar
      dark
      fixed
      elevate-on-scroll
    >
      <img
        height="100px"
        width="100px"
        id="logo"
        src="/logo.svg"
      />
      <v-tabs centered dark color="accent" background-color="#272727">
        <v-tab
          :to="routes[0].to" router exact
        >
          {{ routes[0].title }}
        </v-tab>
      </v-tabs>
      <v-tabs centered dark color="accent" background-color="#272727">
        <v-tab
          :to="routes[1].to" router exact
        >
          {{ routes[1].title }}
        </v-tab>
      </v-tabs>


    </v-app-bar>

    <v-main>
      <v-container fluid>
        <Nuxt/>
      </v-container>
    </v-main>

    <v-footer id="footer" fixed app>
      <v-row justify="center">
        <img
          class="ma-2 pa-1"
          height="40px"
          width="40px"
          id="logoFooter"
          src="/logo_footer.svg"
        />
        <v-col class="text-left align-self-center">
          <span class="copyright">Tourangeau GYM Club &copy; {{ new Date().getFullYear() }} - </span>
          <span class="mentionsLegales">Mentions legales</span>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>

export default {
middleware({route, redirect}) {
    console.log(route)
    if(route.path === '/') {
      return redirect('/home');
    }
  },
  name: 'DefaultLayout',
  data() {
    return {
      routes: [
        {
          title: "accueil",
          to: '/home'
        },
        {
          title: 'agenda',
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
  position: absolute;
  top: 75%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 999;
}

.v-app-bar {
  background-color: #272727 !important;
}

#footer {
  background-color: #272727;
  color: #00FFFF;
  text-shadow: 1px 0 0 #662D91 !important;
}

.mentionsLegales:hover {
  cursor: pointer;
  color: #E800A2;
  text-decoration: underline;
}

</style>
