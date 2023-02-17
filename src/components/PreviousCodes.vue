<template>
  <v-sheet
    rounded="lg"
    height="500"
  >
    <v-row class="my-2">
      <v-col cols="1">
        <v-list class="text-center">
          <v-header>
            Delete
          </v-header>
        </v-list>
      </v-col>
      <v-col cols="9">
        <v-header class="text-center">Previous Codes</v-header>
        <v-list color="transparent" class="overflow-y-auto" max-height="400">
          <v-list-item
            v-for="n in 10"
            :key="n"
          >
            <v-list-item-content>
              <v-list-item-title>
                {{ n }} - {{ n }} - {{ n }} - {{ n }} - {{ n }} 
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item id="last">
            <v-list-content>
              <v-list-title>
                Last one
              </v-list-title>
            </v-list-content>
          </v-list-item>
        </v-list>
      </v-col>
      <v-col cols="2">
        <v-list class="text-center">
          <v-header>
            Amount of numbers correct
          </v-header>
        </v-list>
      </v-col>
    </v-row>
  </v-sheet>
</template>


<script>
export default {
    name: "PreviousCodes",
}
</script>