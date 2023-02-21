<template>
  <v-sheet
    rounded="lg"
    height="500"
  >
    <v-row justify="space-around"> 
      <v-col md="2">
        <v-sheet class="text-center">
          <div class="text-h4">
            Delete
          </div>
        </v-sheet>
      </v-col>
      <v-col md="6">
        <v-sheet class="text-center">
          <div class="text-h4">
            Previous Codes
          </div>
        </v-sheet>
      </v-col>
      <v-col md="2">
        <v-sheet class="text-center">
          <div class="text-h4">
            Correct
          </div>
        </v-sheet>
      </v-col>
    </v-row>
    <v-divider class="my-2"></v-divider>
    <v-list class="overflow-y-auto" max-height="400">
      <v-list-item-group>
        <template>
          <v-list-item
            v-for="n in codes"
            :key="n.id"
            :class="'previousCode'"
          >
            <v-row justify="space-around">
              <v-col md="2" class="d-flex justify-center" style="flex-direction: column;">  
                <v-btn color="error" plain>
                  Delete
                </v-btn>
              </v-col>
              <v-col md="6">
                <v-sheet class="d-flex justify-space-around">
                  <v-card class="pa-2 ma-2"
                    v-for="i in 5"
                    :key="i"
                  >
                  <div class="text-h5">
                    {{ n.numbers[i-1] }}
                  </div>
                  </v-card>
                </v-sheet>
              </v-col>
              <v-col md="2">
                <v-sheet class="d-flex justify-space-around">
                  <v-card class="pa-2 ma-2">
                    <div class="text-h5">
                      {{ n.correct }}
                    </div>
                  </v-card>
                </v-sheet>
              </v-col>
            </v-row>
          </v-list-item>
        </template>
      </v-list-item-group>
    </v-list>
  </v-sheet>
</template>


<script>
export default {
    name: "PreviousCodes",
    props: {
      codes: Array
    }
}
</script>