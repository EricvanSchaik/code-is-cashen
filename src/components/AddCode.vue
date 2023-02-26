<template>
  <v-container style="padding:0px">
    <v-sheet rounded="lg" class="pt-5 pb-1">
      <v-row justify="space-around">
        <v-col md="2">
        </v-col>
        <v-col md="6">
          <v-sheet class="d-flex justify-space-around mr-4" color="transparent">
            <v-text-field outlined style="max-width: 5%;" @input="addNumber($event, i)" @keypress="validateNumber" maxlength="1"
              v-for="i in 5"
              :key="i"
              :id="'code'+i.toString()"
            >
            </v-text-field>
          </v-sheet>
        </v-col>
        <v-col md="2">
          <v-sheet class="d-flex justify-space-around" color="transparent" style="margin-right: 50px">
            <v-text-field outlined style="max-width: 20%" maxlength="1" @input="addCorrect" @keypress="validateCorrect"></v-text-field>
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

function compareArrays(ar1, ar2) {
  return JSON.stringify(ar1) == JSON.stringify(ar2)
}

export default {
  name: "AddCode",
  data: () => ({
    numbers: [null, null, null, null, null],
    correct: null,
  }),
  props: {
    prevCodes: Array
  },
  methods: {
    addCode() {
      let codeExists = false
      for (let codeIndex = 0; codeIndex < this.prevCodes.length; codeIndex++) {
        let code = this.prevCodes[codeIndex]
        if (compareArrays(code.numbers, this.numbers)) {
          codeExists = true
          alert('This code has already been entered')
        }
      }
      if (this.numbers.some(el => el === null) || !this.correct) {
        alert('Please fill in all five digits and how many are correct')
      }
      if (!this.numbers.some(el => el === null) && this.correct && this.correct < 6 && !codeExists) {
        this.$emit('addCode', [...this.numbers], this.correct)
        this.$nextTick(() => {
          let pc = document.getElementsByClassName('previousCode')
          return pc.item(pc.length - 1).scrollIntoView()
        })
      }
    },
    addNumber(number, i) {
      if (/^\d$/.test(number.toString())) {
        this.numbers[i-1] = number.toString()
      }
    },
    validateNumber(event) {
      if (!/^\d$/.test(event.key.toString())) {
        event.preventDefault();
      }
    },
    addCorrect(number) {
      if (/^\d$/.test(number.toString()) && number < 5) {
        this.correct = number.toString()
      }
    },
    validateCorrect(event) {
      if (!/^\d$/.test(event.key.toString()) || event.key.toString() > 4) {
        event.preventDefault();
      }
    }
  },
  emits: ['code']
}
</script>