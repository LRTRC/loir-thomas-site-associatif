<template>
  <v-card id="customHeaderCard" class="pt-12 pt-md-0">
    <v-row>
      <v-col cols="12" md="8" class="align-self-center text-center">
        <v-row>
          <v-col class="pt-0 my-0">
            <h1>
              <span class="titleH1">GYM</span> <span class="titleH1">CLUB</span>
            </h1>
          </v-col>
        </v-row>
        <v-row>
          <v-col class="pt-0 my-0">
            <v-card-subtitle class="subtitle pt-0 my-0">
              {{ subtitle }}
            </v-card-subtitle>
          </v-col>
        </v-row>
      </v-col>

      <v-col id="imgColumn" cols="12" md="4" lg="3">
        <v-img
          class="ma-2"
          src="../banner.png"
        />
      </v-col>


    </v-row>
    <v-row>
      <v-col>

      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  name: "customHeader",
  props: {
    title: {
      type: String,
      default: '',
    },
    subtitle: {
      type: String,
      default: '',
    },
  },
}
</script>

<style scoped>

@media (max-width: 959px) {
  #imgColumn {
    display: none !important;
  }
}

#customHeaderCard {
  background-color: #272727;
  border-radius: 0 !important;
}

.titleH1 {
  color: white;
}

.subtitle {
  color: #C8B1DD;
  font-size: 1.6em !important;
}
</style>
