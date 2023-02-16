<template>
  <v-form @submit="submit">
      <v-btn type="submit">Submit</v-btn>
  </v-form>
</template>

<script>
export default {
  name: "CodeForm",
  methods: {
    submit() {
      alert('Subbmitted!')
    }
  }
}
</script>