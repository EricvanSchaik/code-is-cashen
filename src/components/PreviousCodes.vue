<template>
  <v-sheet
    min-height="70vh"
    rounded="lg"
  >
    <v-card>
      <v-list>
        <v-subheader>Previous Codes</v-subheader>
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
      </v-list>
    </v-card>
  </v-sheet>
</template>


<script>
export default {
    name: "PreviousCodes"
}
</script>