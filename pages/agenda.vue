<template>
  <div>

    <v-row>
      <v-col class="mt-4 px-0">
        <CustomHeader :title="titles[0]" :subtitle="subtitles"/>
      </v-col>
    </v-row>

    <v-row class="ms-4" justify="center">
      <v-col cols="12" md="10">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2701.1418288301124!2d0.6823868335054476!3d47.38966554431728!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47fcd5b7b725aec5%3A0x652b0c6527606376!2s22%20Bd%20B%C3%A9ranger%2C%2037000%20Tours!5e0!3m2!1sfr!2sfr!4v1657200550848!5m2!1sfr!2sfr"
          width="100%" height="400" style="border:0;" allowfullscreen="" loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"></iframe>
      </v-col>
    </v-row>

    <v-row class="my-4">
      <v-col offset="1">
        <h2>
          {{ titles[1].toUpperCase() }}
        </h2>
      </v-col>
    </v-row>

    <v-row justify="center" class="my-4">
      <v-col cols="10" md="8">
        <v-card flat>
          <v-window
            v-model="onBoarding"
          >
            <v-window-item
              v-for="(event, i) in events"
              :key="i">
              <v-card
                height="100%"
                width="100%"
                flat
              >
                <v-row class="ma-4" justify="center">
                  <v-col cols="12" sm="8" md="6">
                    <img
                      height="100%"
                      width="100%"
                      :src="event.img"
                    />
                  </v-col>
                  <v-col cols="12" md="6" class="align-self-center">
                    <v-row>
                      <v-col>
                        <p class="py-4 text-left">
                          {{ event.text }}
                        </p>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col class="text-right">
                        <h3>
                          {{ event.title }}
                        </h3>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col class="text-right">
                        <p>
                          <span class="events">{{ event.theme }}</span>
                        </p>
                      </v-col>
                    </v-row>
                  </v-col>
                </v-row>

              </v-card>
            </v-window-item>
          </v-window>

          <v-card-actions class="justify-space-between py-4">
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
                v-for="(event, i) in events"
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

  </div>
</template>

<script>
import CustomHeader from '../components/customHeader.vue';
import CustomCard from '../components/customCard.vue';
import {mdiChevronDoubleLeft, mdiChevronDoubleRight, mdiRecord} from '@mdi/js';

export default {
  name: "agenda",
  components: {CustomHeader, CustomCard},
  data() {
    return {
      onBoarding: 0,
      icons: [mdiChevronDoubleLeft, mdiChevronDoubleRight, mdiRecord],
      searchField: '',
      selectedTheme: null,
      titles: ['tourangeau gym club', 'évènements'],
      subtitles: 'Listes des évènements',
      events: [
        {
          title: 'Portes ouvertes 2022',
          text: "Le GYM Club sonne la cloche de la rentrée samedi 12 septembre 2022. Le gymnase ouvrira grand " +
            "ses portes au public de 14 h à 17 h pour les inscriptions. Loisirs, compétition, performance pour adultes et enfants",
          theme: 'portes ouvertes',
          img: '../open-day.jpeg',
        },
        {
          title: 'Open CrossFit du Val de Loire 2022',
          text: "L'Open CrossFit du Val de Loire se tiendra le 18 novembre 2022 et donnera aux athlètes CrossFit de toute la région la chance de se mettre au défi et " +
            "de briller sur la scène française.",
          theme: 'compétition',
          img: '../open-crossfit.jpeg',
        },
        {
          title: 'Démonstration publique de pilates',
          text: "Rencontrez vos professionnels du bien-être et tester gratuitement ces activités" +
            "L'occasion de rappeler les bienfaits du pilates sur le corps. RDV le 5 août 2022 à 14h au parc Montsouris",
          theme: 'exhibition',
          img: '../exhibition.jpeg',
        },
      ],
    }
  },
  methods: {
    next() {
      this.onBoarding = this.onBoarding + 1 === this.events
        ? 0
        : this.onBoarding + 1
    },
    prev() {
      this.onBoarding = this.onBoarding - 1 < 0
        ? this.events - 1
        : this.onBoarding - 1
    },
  },
}
</script>


<style scoped>
.events {
  color: #662D91;
  font-family: 'Barlow-Black', sans-serif;
  font-style: italic;
  font-size: 1em !important;
  letter-spacing: 5px !important;
}
</style>
