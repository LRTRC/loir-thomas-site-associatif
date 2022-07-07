<template>
  <div>

    <v-row>
      <v-col>
        <CustomHeader :title="headerTitle" :subtitle="headerSubTitle" />
      </v-col>
    </v-row>

    <v-divider />

    <v-row justify="center">
      <v-col cols="12" md="10">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2701.1418288301124!2d0.6823868335054476!3d47.38966554431728!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47fcd5b7b725aec5%3A0x652b0c6527606376!2s22%20Bd%20B%C3%A9ranger%2C%2037000%20Tours!5e0!3m2!1sfr!2sfr!4v1657200550848!5m2!1sfr!2sfr"
          width="100%" height="400" style="border:0;" allowfullscreen="" loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"></iframe>
      </v-col>
    </v-row>

    <v-divider />

    <v-row>
      <v-col>
        <v-text-field v-model="searchField" label="Rechercher ..." clearable></v-text-field>
      </v-col>
      <v-col>
        <v-select v-model="selectedTheme" :items="themes" label="Thèmes" clearable></v-select>
      </v-col>
      <v-col>
        <v-menu v-model="datePickerMenu" :close-on-content-click="false" :nudge-right="40" transition="scale-transition"
          offset-y min-width="auto">
          <template v-slot:activator="{ on, attrs }">
            <v-text-field v-model="date" label="Choisir une date" prepend-icon="mdi-calendar" readonly v-bind="attrs"
              v-on="on" clearable></v-text-field>
          </template>
          <v-date-picker v-model="date" @input="datePickerMenu = false"></v-date-picker>
        </v-menu>
      </v-col>
    </v-row>

    <v-divider />

    <v-row justify="center">
      <v-col cols="12" sm="6" md="4"
        v-if="selectedTheme === null && date === null || selectedTheme === 'portes ouvertes' && date === '2022-09-12' || date === '2022-09-12' && selectedTheme === null || selectedTheme === 'portes ouvertes' && date === null">
        <CustomCard :subtitle="subtitles[0]" :paragraph="paragraphs[0]" :src="src[0]" />
      </v-col>
      <v-col cols="12" sm="6" md="4"
        v-if="selectedTheme === null && date === null || selectedTheme === 'compétition' && date === '2022-11-18' || date === '2022-11-18' && selectedTheme === null || selectedTheme === 'compétition' && date === null">
        <CustomCard :subtitle="subtitles[1]" :paragraph="paragraphs[1]" :src="src[1]" />
      </v-col>
      <v-col cols="12" sm="6" md="4"
        v-if="selectedTheme === null && date === null || selectedTheme === 'exhibition' && date === '2022-08-05' || date === '2022-08-05' && selectedTheme === null || selectedTheme === 'exhibition' && date === null">
        <CustomCard :subtitle="subtitles[2]" :paragraph="paragraphs[2]" :src="src[2]" />
      </v-col>
    </v-row>

  </div>
</template>

<script>
import CustomHeader from '../components/customHeader.vue';
import CustomCard from '../components/home/customCard.vue';
export default {
  name: "agenda",
  components: { CustomHeader, CustomCard },
  data() {
    return {
      searchField: '',
      selectedTheme: null,
      themes: ['portes ouvertes', 'compétition', 'exhibition'],
      datePickerMenu: false,
      date: null,
      headerTitle: 'tourangeau gym club',
      headerSubTitle: 'Listes des évènements',
      src: [
        '../open-day.jpeg',
        '../open-crossfit.jpeg',
        '../exhibition.jpeg',
      ],
      subtitles: [
        "Portes ouvertes 2022",
        "Open CrossFit du Val de Loire 2022",
        "Démonstration publique de pilates",

      ],
      paragraphs: [
        "Le GYM Club sonne la cloche de la rentrée samedi 12 septembre 2022. Le gymnase ouvrira grand " +
        "ses portes au public de 14 h à 17 h pour les inscriptions. Loisirs, compétition, performance pour adultes et enfants",
        "L'Open CrossFit du Val de Loire se tiendra le 18 novembre 2022 et donnera aux athlètes CrossFit de toute la région la chance de se mettre au défi et " +
        "de briller sur la scène française.",
        "Rencontrez vos professionnels du bien-être et tester gratuitement ces activités" +
        "L'occasion de rappeler les bienfaits du pilates sur le corps. RDV le 5 août 2022 à 14h au parc Montsouris"
      ],
    }
  },
}
</script>


<style scoped>
</style>
