<template>
  <v-sheet
    rounded="lg"
    min-height="268"
  >
    <v-list color="transparent">
      <v-list-item
        v-for="n in this.possibleCodes"
        :key="n.index"
      >
        <v-list-item-content>
          <v-list-item-title>
            {{ n }}
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-divider class="my-2"></v-divider>
      <v-list-item
        link
      >
        <v-list-item-content>
          <v-list-item-title>
            Next
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-sheet>
</template>

<script>
import { setPowerset } from 'mathjs'

function findPowerset(maxIndex) {
  let set = []
  for (let i = 0; i < maxIndex; i++) {
    set.push(i)
  }
  let result = setPowerset(set)
  if (set.length == 0) {
    result = [[]]
  }
  return result
}

function nextNumber(code, index, number) {
  number++
  while (number > 9) {
    index--
    if (index == -1) {
      return [undefined, undefined]
    }
    number = parseInt(code[index])
    number++
  }
  return [index, number]
}

function checkNumberValid(code, prevCodes, currentIndex) {
  const powerSet = findPowerset(currentIndex)
  for (const set in powerSet) {
    for (let prevIndex = 0; prevIndex < prevCodes.length; prevIndex++) {
      const prevCode = prevCodes[prevIndex]
      let similarCode = true
      for (const index in set) {
        if (!(prevCode.numbers[index] == code[index])) {
          similarCode = false
        }
      }
      if (!(prevCode.numbers[currentIndex] == code[currentIndex])) {
        similarCode = false
      }
      if (similarCode) {
        if (prevCode.correct <= set.length) {
          return false
        }
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
        if (this.prevCodes.length > 0) {
          let index = 0
          let number = 0
          let code = []
          while (result.length < 10) {
            code[index] = number.toString()
            if (checkNumberValid(code, this.prevCodes, index)) {
              if (index == 4) {
                result.push([...code])
                console.log(result)
                ;[index, number] = nextNumber(code, index, number)
                if (!index) {
                  return result
                }
              }
              else {
                index++
              }
            }
            else {
              [index, number] = nextNumber(code, index, number)
              if (index == undefined) {
                return result
              }
            }
          }
        }
        return result
      }
    }
}
</script>