<template>
  <div>
    <v-row>
      <v-col class="mt-4 px-0">
        <custom-header :title="headerTitle" :subtitle="headerSubTitle"/>
      </v-col>
    </v-row>

    <v-row class="mx-1 my-4 ma-sm-4">
      <v-col cols="12" md="6">
        <v-img
          src="/who_we_are.png"
          aspect-ratio="1.4"
        />
      </v-col>
      <v-col cols="12" md="6" class="align-self-center">
        <v-row>
          <v-col>
            <h2>
              {{ titles[0].toUpperCase() }}
            </h2>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" md="8">
            <p>
              {{ paragraphs[3] }}
            </p>
          </v-col>
        </v-row>
      </v-col>
    </v-row>

    <v-row class="my-4 ma-md-4">
      <v-col>
        <v-card color="#C8B1DD" style="border-radius: 25px" class="ma-auto pa-4">
          <v-row>
            <v-col offset="1">
              <h2>
                {{ titles[1].toUpperCase() }}
              </h2>
            </v-col>
          </v-row>
          <v-row class="ma-4">
            <v-col class="px-0 px-md-2" cols="12" md="4">
              <custom-card class="my-3 ma-sm-3" :subtitle="subtitles[0]" :paragraph="paragraphs[0]" :src="src[0]"/>
            </v-col>
            <v-col class="px-0 px-md-2" cols="12" md="4">
              <custom-card class="my-3 ma-sm-3" :subtitle="subtitles[1]" :paragraph="paragraphs[1]" :src="src[1]"/>
            </v-col>
            <v-col class="px-0 px-md-2" cols="12" md="4">
              <custom-card class="my-3 ma-sm-3" :subtitle="subtitles[2]" :paragraph="paragraphs[2]" :src="src[2]"/>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>

    <v-row class="mt-4" >
      <v-col offset="1">
        <h2>
          {{ titles[2].toUpperCase() }}
        </h2>
      </v-col>
    </v-row>

    <v-row justify="center" >
      <v-col cols="12" md="8">
        <v-card flat>
          <v-window
            v-model="onBoarding"
          >
            <v-window-item
              v-for="(coach, i) in coaches"
              :key="i">
              <v-card
                height="100%"
                width="100%"
                flat
              >
                <v-row justify="center">
                  <v-col cols="8" sm="6" >
                    <img
                      height="100%"
                      width="100%"
                      :src="coach.img"
                    />
                  </v-col>
                  <v-col cols="8" md="6" class="align-self-center">
                    <v-row>
                      <v-col>
                        <p class="py-4 text-left">
                          {{ coach.testimony }}
                        </p>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col class="text-right">
                        <h3>
                          {{ coach.name }}
                        </h3>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col class="text-right">
                        <p>
                          <span class="jobs">{{ coach.job }}</span>
                        </p>
                      </v-col>
                    </v-row>
                  </v-col>
                </v-row>

              </v-card>
            </v-window-item>
          </v-window>

          <v-card-actions class="justify-space-between my-4">
            <v-btn
              text
              @click="prev"
            >
              <v-icon
                x-large
                color="primary"
              >
                {{ icons[0] }}
              </v-icon>
            </v-btn>
            <v-item-group
              v-model="onBoarding"
              class="text-center"
              mandatory
            >
              <v-item
                v-for="(coach, i) in coaches"
                :key="i"
                v-slot="{ active, toggle }"
              >
                <v-btn
                  :input-value="active"
                  icon
                  @click="toggle"
                >
                  <v-icon>
                    {{ icons[2] }}
                  </v-icon>
                </v-btn>
              </v-item>
            </v-item-group>
            <v-btn
              text
              @click="next"
            >
              <v-icon
                x-large
                color="primary"
              >
                {{ icons[1] }}
              </v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>


    <v-row>
      <v-col offset="1">
        <h2>
          {{ titles[3].toUpperCase() }}
        </h2>
      </v-col>
    </v-row>
    <v-row class="my-4" justify="center">
      <v-col cols="8" sm="4" lg="3" class="text-center">
        <v-card class="customCardShadow" raised rounded="xl">
          <v-avatar size="65%" class="pa-4">
            <img :src="src[3]"/>
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
import {mdiChevronDoubleLeft, mdiChevronDoubleRight, mdiRecord} from '@mdi/js';

export default {
  name: "home",
  components: {
    customCard,
    customHeader,
  },
  data() {
    return {
      onBoarding: 0,
      icons: [mdiChevronDoubleLeft, mdiChevronDoubleRight, mdiRecord],
      coaches: [
        {
          name: 'Georges Delapierre',
          job: 'coach pilates - fitness',
          testimony: 'Coach de body balance depuis 5 ans, j’ai une véritable passion pour ce letier, aider les gens à s’améliorer physiquement et mentalement en retrouvant une bonne tonicité, je vois chez les personnesque j’entraine une véritable évolution physique et mentale.\n',
          img: '/coach_georges.png',
        },
        {
          name: 'Nathalie Nemann',
          job: 'coach body balance - yoga',
          testimony: 'Coach de body balance depuis 5 ans, j’ai une véritable passion pour ce letier, aider les gens à s’améliorer physiquement et mentalement en retrouvant une bonne tonicité, je vois chez les personnesque j’entraine une véritable évolution physique et mentale.\n',
          img: '/coach_nathalie.png',

        },
        {
          name: 'Alexis Seros',
          job: 'coach ft - crossfit',
          testimony: 'Coach de body balance depuis 5 ans, j’ai une véritable passion pour ce letier, aider les gens à s’améliorer physiquement et mentalement en retrouvant une bonne tonicité, je vois chez les personnesque j’entraine une véritable évolution physique et mentale.\n',
          img: '/coach_alexis.png',

        },
      ],
      headerTitle: 'GYM CLUB',
      headerSubTitle: 'Complexe sportif mixt',
      titles: ['qui sommes-nous ?', 'programmes', 'l\'équipe', 'témoignage'],
      src: [
        '/functional_training.svg',
        '/pilates.svg',
        '/body_balance.svg',
        '/woman_avatar.jpeg',
      ],
      subtitles: [
        'functionnal training',
        'pilates',
        'body balance',
        'qui sommes-nous ?',
      ],
      paragraphs: [
        'Nos séances sont basées sur de la préparation physique et sont adaptées à ' +
        'tous les niveaux et conditions physiques.\n' +
        'Le FT vise à retrouver les aptitudes et gestes naturels nécessaires au quotidien.\n' +
        'Il permet de prévenir les blessures grâce au renforcement des capacités physique du pratiquant.',
        'Le Pilates est une méthode de renforcement des muscles profonds, responsables de la posture. ' +
        'Les muscles profonds sont les muscles du centre, qui se situent entre les côtes et le bassin, ' +
        'et tout autour de la colonne vertébrale (abdominaux, plancher pelvien et les muscles du dos).',
        'Le Body Balance est un cours de fitness complet ' +
        'et varié qui alterne 3 phases de : Yoga ; Taï-chi ; Pilates .L’idée du Body Balance ' +
        'est de créer un programme efficace et accessible pour améliorer sa tonicité, ' +
        'réduire les douleurs musculaires et réduire son stress. Cette pratique est excellente remise en forme.',
        'Le TOURANGEAU GYM CLUB est un complexe de 500m2 basé à Tours.\n' +
        'Notre salle est dédiée aux arts pratiques mixtes, au bien-être ainsi qu\'au ' +
        'développement personnel. Nous comptons plus d’une dizaine de disciplines ' +
        'de sports et préparation physique générale (Functionnal training, Pilat, CrossFit, Fitness).' +
        ' De plus, nous proposons un réel suivi bien-être à travers nos disciplines ' +
        '(yoga, méditation, cours privés) ainsi que nos prestataires ' +
        '(nutrition, sophrologie, naturopathie, kinésithérapeute).',
      ],
      testimonialTitle: 'Alexandra',
      testimonialBody: 'Super club, excellente prise en charge, progression garantie',
    }
  },
  methods: {
    next() {
      this.onBoarding = this.onBoarding + 1 === this.coaches
        ? 0
        : this.onBoarding + 1
    },
    prev() {
      this.onBoarding = this.onBoarding - 1 < 0
        ? this.coaches - 1
        : this.onBoarding - 1
    },
  },
}
</script>

<style scoped>

.jobs {
  color: #662D91;
  font-family: 'Barlow-Black', sans-serif;
  font-style: italic;
  font-size: 1em !important;
}

.customCardShadow {
  box-shadow: 4px 8px 16px 0 rgba(31, 38, 135, 0.37) !important;
}
</style>
