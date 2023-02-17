<template>
  <container>
    <v-row justify="space-around">
      <v-col md="2">
      </v-col>
      <v-col md="6">
        <v-sheet class="d-flex justify-space-around" color="transparent">
          <v-card class="pa-2 ma-2"
            v-for="i in 5"
            :key="i"
          >
          <div class="text-h5">
            {{ i }}
          </div>
          </v-card>
        </v-sheet>
      </v-col>
      <v-col md="2">
        <v-sheet class="d-flex justify-space-around" color="transparent">
          <v-card class="pa-2 my-2 mr-11">
            <div class="text-h5">
              0
            </div>
          </v-card>
        </v-sheet>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-btn @click="scroll">Add Code</v-btn>
    </v-row>
  </container>
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