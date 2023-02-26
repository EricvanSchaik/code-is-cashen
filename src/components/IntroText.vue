<template>
  <v-sheet rounded="lg" class="text-center py-8 px-6">
    <h1 class="display-2 font-weight-bold mb-3">
      Welcome to the Code = Cashen Helper!
    </h1>
    Starting from Monday, 29th of August 2022, Radio 583 has introduced a new game on their morning show, called Code = Cashen. The goal of this game is to guess a 5-digit number, which leads to a cash prize of 10.000 euros. Every morning at 7:45, a caller can make a guess, and the first caller who guesses the correct number wins the cash prize. If you guess wrong, the hosts are kind enough to tell you how many of the digits are correct, but not which digits. Click the button in the top-right corner for more information. <br> <br>
    This web app serves as a helper to participants of the game. Below you can fill in codes that have been guessed earlier, along with the number of correct digits. Based on these previous numbers, a list of possible numbers is calculated and shown on the left. Good luck!
  </v-sheet>
</template>

<script>
export default {
  name: "IntroText"
}
</script>