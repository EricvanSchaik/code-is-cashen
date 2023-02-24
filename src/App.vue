<template>
  <v-app>
    <v-app-bar
      app
      color="#000000"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://images.ctfassets.net/xb7h1e8hmxoz/3Sgf12hLpf8BVtxrz93rDW/811e384eaf7e724dac3d45ef09f12e1f/MicrosoftTeams-image__3_.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://www.538.nl/acties/speel-mee-met-code-cashen-en-maak-kans-op-eur-10-000"
        target="_blank"
        text
      >
        <span class="mr-2">More Information</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col cols="2">
            <CodeOptions :prevCodes="codes"/>
          </v-col>
          <v-col>
            <IntroText/>
            <v-divider class="my-2"></v-divider>
            <PreviousCodes :codes="codes" @deleteCode="deleteCode"/>
            <v-divider class="my-2"></v-divider>
            <AddCode @addCode="addCode"/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import CodeOptions from './components/CodeOptions.vue';
import PreviousCodes from './components/PreviousCodes.vue';
import IntroText from './components/IntroText.vue';
import AddCode from './components/AddCode.vue';

let id = 0

export default {
  name: 'App',

  components: {
    CodeOptions,
    PreviousCodes,
    IntroText,
    AddCode,
  },

  data: () => ({
    codes: []
  }),

  methods: {
    addCode(numbers, correct) {
      this.codes.push({
        id: id++,
        numbers: numbers,
        correct: correct
      })
    },
    deleteCode(id) {
      this.codes = this.codes.filter(code => code.id !== id)
    }
  }
};
</script>
