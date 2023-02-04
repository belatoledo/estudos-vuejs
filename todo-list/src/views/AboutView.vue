<template>
  <div class="about">
    <h1>This is an about page</h1>

    <v-card>
      <h2>This is a text.</h2>
      <v-icon icon="mdi-home" />
      <v-btn icon="mdi-heart" color="primary"></v-btn>
    </v-card>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
