<template>
  <v-container style="padding:0px">
    <v-sheet rounded="lg" class="pt-5 pb-1">
      <v-row justify="space-around">
        <v-col md="2">
        </v-col>
        <v-col md="6">
          <v-sheet class="d-flex justify-space-around mr-4" color="transparent">
            <v-text-field outlined style="max-width: 5%;" @keypress="addNumber" maxlength="1"
              v-for="i in 5"
              :key="i"
              :id="'code'+i.toString()"
            >
            </v-text-field>
          </v-sheet>
        </v-col>
        <v-col md="2">
          <v-sheet class="d-flex justify-space-around" color="transparent" style="margin-right: 50px">
            <v-text-field outlined style="max-width: 20%" maxlength="1"></v-text-field>
          </v-sheet>
        </v-col>
      </v-row>
    </v-sheet>
    <v-row justify="center" style="margin:20px">
      <v-btn @click="addCode">Add Code</v-btn>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "AddCode",
  methods: {
    addCode() {
      this.$emit('code', '00000')
      this.$nextTick(() => {
        let pc = document.getElementsByClassName('previousCode')
        return pc.item(pc.length - 1).scrollIntoView()
      })
    },
    addNumber(event) {
      if (/^\d$/.test(event.key.toString())) {
        console.log(event.key.toString())
      }
      else {
        event.preventDefault();
      }
    }
  },
  emits: ['code']
}
</script>