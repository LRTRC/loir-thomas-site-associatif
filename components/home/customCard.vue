<template>
  <v-card >
    <v-img
      :src="src"
    />
    <h3>
      {{ subtitle }}
    </h3>
    <p>
      {{ paragraph }}
    </p>
  </v-card>
</template>

<script>
export default {
  name: "customCard",
  props: {
    src: {
      type: String,
      default: '../blank_img.jpeg',
    },
    subtitle: {
      type: String,
      default: '',
    },
    paragraph: {
      type: String,
      default: '',
    }
  }
}
</script>

<style scoped>

</style>
