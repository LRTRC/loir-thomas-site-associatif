<template>
  <v-card id="customCard" elevation="5">
    <v-row class="customCardRowImg">
      <v-col>
        <img
          height="75px"
          width="100%"
          :src="src"
        />
      </v-col>
      <v-col>
        <h3 class="mt-4">
          {{ subtitle.toUpperCase() }}
        </h3>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <p class="ma-4">
          {{ paragraph }}
        </p>
        <p class="offset-2 pt-4">
          <span class="link">Inscrivez-vous dès maintenant !</span>
        </p>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  name: "customCard",
  props: {
    src: {
      type: String,
      default: '/blank_img.jpeg',
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

#customCard {
  border-radius: 25px;
  box-shadow: 4px 8px 16px 0 rgba(31, 38, 135, 0.37) !important;
}

.customCardRowImg {
  height: 75px !important;
}

.link {
  color: #662D91;
  font-weight: bolder;
}

.link:hover {
  cursor: pointer;
  color: #E800A2;
  text-decoration: underline;
}
</style>
