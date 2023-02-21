<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col cols="2">
            <CodeOptions/>
          </v-col>
          <v-col>
            <IntroText/>
            <v-divider class="my-2"></v-divider>
            <PreviousCodes :codes="codes"/>
            <v-divider class="my-2"></v-divider>
            <AddCode @code="addCode"/>
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
    addCode(code) {
      this.codes.push({
        id: id++,
        numbers: code,
        correct: 0
      })
    }
  }
};
</script>
