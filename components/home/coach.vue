<template>
  <v-card class="coach" color="rgb(18,18,18)">
    <v-img
      :src="src"
    />
    <h3>
      {{ subtitle.toUpperCase() }}
    </h3>
    <p>
      {{ paragraph }}
    </p>
  </v-card>
</template>

<script>
export default {
  name: "coach",
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
.coach {

}
</style>
