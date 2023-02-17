<template>
  <v-btn @click="scroll">goto</v-btn>
</template>

<script>
export default {
  name: "AddCode",
  methods: {
    scroll() {
      this.$nextTick(() => document.getElementById('last').scrollIntoView())
    }
  }
}
</script>