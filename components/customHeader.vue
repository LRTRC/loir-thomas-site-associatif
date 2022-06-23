<template>
<v-card>
  <h1>
    {{ title }}
  </h1>
  <v-card-subtitle class="HeaderSubtitle">
    {{ subtitle }}
  </v-card-subtitle>
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

</style>
