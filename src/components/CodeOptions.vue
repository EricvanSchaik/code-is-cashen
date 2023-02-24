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

// function compareArrays(ar1, ar2) {
//   return JSON.stringify(ar1) === JSON.stringify(ar2)
// }

// function findAllSubsets(size, maxIndex) {
//   return []
// }

// function checkNumberValid(code, prevCodes, index) {
//   for (let subsetSize = 1; subsetSize < index + 1; subsetSize++) {
    
//   }

//   // Check current index
//   for (let prevIndex = 0; prevIndex < prevCodes.length; prevIndex++) {
//     if (prevCodes[prevIndex].numbers[index] == code[index]) {
//       if (!prevCodes[prevIndex].correct > 0) {
//         return false
//       }
//     }
//   }

//   // Check previous indices
//   for (let checkIndex = index - 1; checkIndex >= 0; checkIndex--) {
//     for (let prevIndex = 0; prevIndex < prevCodes.length; prevIndex++) {
//       const prevCode = prevCodes[prevIndex]
//       if (compareArrays([prevCode.numbers[checkIndex], prevCode.numbers[index]], [code[checkIndex], code[index]])) {
//         if (!prevCodes[prevIndex].correct > 1) {
//           return false
//         }
//       }
//       if (compareArrays(prevCode.numbers.slice(checkIndex, index + 1), code.slice(checkIndex, index + 1))) {
//         if (!prevCode.correct > code.slice(checkIndex, index + 1).length) {
//           return false
//         }
//       }
//     }
//   }
//   return true
// }


export default {
    name: "CodeOptions",
    props: {
      prevCodes: Array
    },
    computed: {
      possibleCodes() {
        let result = []
        // if (this.prevCodes.length > 0) {
        //   let index = 0
        //   let number = 0
        //   let code = []
        //   while (result.length < 10) {
        //     if (code[index] == undefined) {
        //       code[index] = number.toString()
        //     }
        //     if (checkNumberValid(code, this.prevCodes, index)) {
        //       if (index == 5) {
        //         result.push(code)
        //         number++
        //         while (number > 9) {
        //           code[index] = undefined
        //           index--
        //           if (index == -1) {
        //             return result
        //           }
        //           number = code[index]
        //           number++
        //         }
        //       }
        //       else {
        //         index++
        //       }
        //     }
        //     else {
        //       number++
        //       while (number > 9) {
        //         code[index] = undefined
        //         index--
        //         if (index == -1) {
        //           return result
        //         }
        //         number = code[index]
        //         number++
        //       }
        //     }
        //   }
        // }
        for (let i = 0; i < 10; i++) {
          result.push('00000')
        }
        return result
      }
    }
}
</script>