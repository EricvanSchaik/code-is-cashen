<template>
  <v-sheet
    rounded="lg"
    min-height="268"
  >
    <v-list color="transparent">
      <v-list-item
        v-for="n in 10"
        :key="n"
      >
        <v-list-item-content>
          <v-list-item-title>
            List Item {{ n }}
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
export default {
    name: "CodeOptions"
}
</script>