<template>
  <v-sheet
    rounded="lg"
  >
    <v-list color="transparent">
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
  </v-sheet>
</template>


<script>
export default {
    name: "PreviousCodes"
}
</script>