<template>
  <v-container style="padding:0px">
    <v-sheet rounded="lg" class="pt-5 pb-1">
      <v-row justify="space-around">
        <v-col md="2">
        </v-col>
        <v-col md="6">
          <v-sheet class="d-flex justify-space-around mr-4" color="transparent">
            <v-text-field outlined style="max-width: 5%;"
              v-for="i in 5"
              :key="i"
            >
            </v-text-field>
          </v-sheet>
        </v-col>
        <v-col md="2">
          <v-sheet class="d-flex justify-space-around mr-8" color="transparent">
            <v-text-field outlined style="max-width: 20%"></v-text-field>
          </v-sheet>
        </v-col>
      </v-row>
    </v-sheet>
    <v-row justify="center" style="margin:20px">
      <v-btn @click="scroll">Add Code</v-btn>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "AddCode",
  methods: {
    scroll() {
      this.$nextTick(() => document.getElementById('last').scrollIntoView())
    }
  }
}
</script>