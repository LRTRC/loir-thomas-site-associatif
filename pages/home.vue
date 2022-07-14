<template>
  <div>
    <v-row>
      <v-col>
        <custom-header :title="headerTitle" :subtitle="headerSubTitle" />
      </v-col>
    </v-row>

    <v-divider />

    <v-row>
      <v-col>
        <h2>
          {{ titles[0].toUpperCase() }}
        </h2>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" sm="6" md="4">
        <custom-card :subtitle="subtitles[0]" :paragraph="paragraphs[0]" :src="src[0]" />
      </v-col>
      <v-col cols="12" sm="6" md="4">
        <custom-card :subtitle="subtitles[2]" :paragraph="paragraphs[2]" :src="src[2]" />
      </v-col>
      <v-col cols="12" sm="6" md="4">
        <custom-card :subtitle="subtitles[1]" :paragraph="paragraphs[1]" :src="src[1]" />
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-img />
      </v-col>
    </v-row>

    <v-divider />

    <v-row>
      <v-col>
        <h2>
          {{ titles[1].toUpperCase() }}
        </h2>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="8" lg="6">
        <v-img :src="src[3]" />
        <v-card>
          <h3>
            {{ subtitles[3].toUpperCase()  }}
          </h3>
          <p>
            {{ paragraphs[3] }}
          </p>
        </v-card>
      </v-col>
    </v-row>

    <v-divider />

    <v-row>
      <v-col>
        <h2>
          {{ titles[2].toUpperCase() }}
        </h2>
      </v-col>
    </v-row>
    <v-row justify="center">
       <v-col cols="12" sm="6" md="4">
        <coach :subtitle="subtitles[5]" :paragraph="paragraphs[5]" :src="src[5]" />
      </v-col>
      <v-col cols="12" sm="6" md="4">
        <coach :subtitle="subtitles[4]" :paragraph="paragraphs[4]" :src="src[4]" />
      </v-col>
      <v-col cols="12" sm="6" md="4">
        <coach :subtitle="subtitles[6]" :paragraph="paragraphs[6]" :src="src[6]" />
      </v-col>
    </v-row>

    <v-divider />

    <v-row>
      <v-col>
        <h2>
          {{ titles[3].toUpperCase() }}
        </h2>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="8" md="4" lg="3" class="text-center">
        <v-card>
          <v-avatar size="65%" class="pa-4">
            <v-img :src="src[7]" />
          </v-avatar>
          <v-card-subtitle>
            {{ testimonialTitle }}
          </v-card-subtitle>
          <v-card-text>
            {{ testimonialBody }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>

import customHeader from '../components/customHeader';
import customCard from "../components/customCard";
import coach from "../components/home/coach";


export default {
  name: "home",
  components: {
    customCard,
    customHeader,
    coach,
  },
  data() {
    return {
      headerTitle: 'tourangeau gym club',
      headerSubTitle: 'complexe sportif mixt - développement personnel - bien-être',
      titles: ['catégories', 'présentation', 'l\'équipe', 'témoignage'],
      src: [
        '../functional_training.jpeg',
        '../pilate.jpeg',
        '../body_balance.jpeg',
        '../who_are_we.jpeg',
        '../coach_georges.png',
        '../coach_nathalie.png',
        '../coach_alexis.png',
        '../woman_avatar.jpeg',
        ],
      subtitles: [
        'functionnal training',
        'pilates',
        'body balance',
        'qui sommes-nous ?',
        'Georges Delapierre',
        'Nathalie Nemann',
        'Alexis Seros',
      ],
      paragraphs: [
        'Nos séances sont basées sur de la préparation physique et sont adaptées à ' +
        'tous les niveaux et conditions physiques.\n' +
        'Le FT vise à retrouver les aptitudes et gestes naturels nécessaires au quotidien.\n' +
        'Il permet de prévenir les blessures grâce au renforcement des capacités physique du pratiquant.',
        'Le Pilates est une méthode de renforcement des muscles profonds, responsables de la posture. ' +
        'Les muscles profonds sont les muscles du centre, qui se situent entre les côtes et le bassin, ' +
        'et tout autour de la colonne vertébrale (abdominaux, plancher pelvien et les muscles du dos).',
        'Le Body Balance est un cours de fitnesLe Body Balance est un cours de fitness complet ' +
        'et varié qui alterne 3 phases de : Yoga ; Taï-chi ; Pilates L’idée du Body Balance ' +
        'est de créer un programme efficace et accessible pour améliorer sa tonicité, ' +
        'réduire les douleurs musculaires et réduire son stress.',
        'Le TOURANGEAU GYM CLUB est un complexe de 500m2 basé à Tours.\n' +
        'Notre salle est dédiée aux arts pratiques mixtes, au bien-être ainsi qu\'au ' +
        'développement personnel. Nous comptons plus d’une dizaine de disciplines ' +
        'de sports et préparation physique générale (Functionnal training, Pilat, CrossFit, Fitness).' +
        ' De plus, nous proposons un réel suivi bien-être à travers nos disciplines ' +
        '(yoga, méditation, cours privés) ainsi que nos prestataires ' +
        '(nutrition, sophrologie, naturopathie, kinésithérapeute).',
        'coach pilates - fitness',
        'coach ft - crossfit',
        'coach body balance - yoga',
      ],
      testimonialTitle: 'Alexandra',
      testimonialBody: 'Super club, excellente prise en charge, progression garantie',
    }
  }
}
</script>

<style scoped>
</style>
