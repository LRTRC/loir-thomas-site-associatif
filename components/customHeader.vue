<template>
  <v-card id="customHeaderCard">
    <v-row>
      <v-col offset="2">
        <h1>
          {{ title.toUpperCase() }}
        </h1>
      </v-col>
    </v-row>
    <v-row>
      <v-col offset="6">
        <v-card-subtitle class="HeaderSubtitle">
          {{ subtitle }}
        </v-card-subtitle>
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
@media (max-width: 700px) {
  #customHeaderCard {
    min-height: 200px;
  }
}
@media (max-width: 1200px) {
  #customHeaderCard {
    min-height: 300px;
  }
}
@media (min-width: 1201px) {
  #customHeaderCard {
    min-height: 400px;
  }
}
#customHeaderCard {
  background-image: url("../static/header.jpeg");
  background-position: center;
  background-size: 100%;

}
</style>
