<template>
  <v-sheet
    class="text-center"
    rounded="lg"
    min-height="268"
  >
    <div class="text-h5 pa-2">
      Possible Codes
    </div>
    <v-divider class="my-2"></v-divider>
    <v-list color="transparent">
      <v-list-item
        v-for="code in this.possibleCodes"
        :key="code.index"
      >
        <v-list-item-content>
          <v-list-item-title>
            <span
              v-for="digit in code.slice(0, code.length - 1)"
              :key="digit.index"
            > {{ digit }} - </span>
            <span> {{ code[code.length-1] }} </span>
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-sheet>
</template>

<script>

function nextCode(code) {
  for (let index = code.length-1; index >= 0; index--) {
    if (code[index] < 9) {
      code[index] = code[index] + 1
      return code
    }
    else {
      code[index] = 0
    }
  }
  return undefined
}

function checkCodeValid(code, prevCodes) {
  if (prevCodes) {
    for (let prevIndex = 0; prevIndex < prevCodes.length; prevIndex++) {
      let prevCode = prevCodes[prevIndex]
      let correct = 0
      for (let index = 0; index < prevCode.numbers.length; index++) {
        if (prevCode.numbers[index] == code[index]) {
          correct++
        }
      }
      if (!(prevCode.correct == correct)) {
        return false
      }
    }
  }
  return true
}


export default {
    name: "CodeOptions",
    props: {
      prevCodes: Array
    },
    computed: {
      possibleCodes() {
        let result = []
        let code = [0,0,0,0,0]
        while (result.length < 10) {
          if (checkCodeValid(code, this.prevCodes)) {
            result.push([...code])
          }
          code = nextCode([...code])
          if (!code) {
            return result
          }
        }
        return result
      }
    }
}
</script>