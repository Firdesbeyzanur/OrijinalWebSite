<template>
        <v-card
    class="mx-auto"
    theme="dark"
    title="Card title"
    text="..."
    variant="tonal"

  >
  <v-toolbar
        dark
      > 
        <v-toolbar-title>Home</v-toolbar-title>
        <v-spacer></v-spacer>
      </v-toolbar>
      <v-card style="color: #8FB996;">
        <h3 class="text-center">
      <br>
        Hello and Welcome!
      <v-spacer></v-spacer>
      I am Firdes Beyzanur Şenocak, and this is my personal website. I share my project contents here.
      <v-spacer></v-spacer>
      Welcome to my website! I am here to share interesting topics, showcase my projects, and share my experiences with you. I hope you enjoy navigating through my site and feel free to contact me.
      <v-spacer></v-spacer>
      Thank you,</h3>
      <br>
      </v-card>
      
      <v-card style="color: #9FC9EB;">
        <h3 class="text-center">
      <br>
      You can learn more about me by visiting my <nuxt-link to="/about">About</nuxt-link> page.
      <v-spacer></v-spacer>
      There, I provide a brief summary about my life.
      <v-spacer></v-spacer>
      If you would like to review my projects, you can visit my <n-link to="portfolio">Portfolio</n-link> page. There, I showcase some of my own projects and provide detailed information about them. 
      <v-spacer></v-spacer>
      Additionally, my CV is also available on my website. By clicking the button, you can review my CV and learn more about me.
      <v-spacer></v-spacer>
      </h3>
      <!-- Eklenecek -->
      <v-btn>Downland CV</v-btn>
      <br>
      </v-card>

      <v-card style="color: #9FC9EB;">
        <h3 class="text-center">
      <br>
      You can learn more about me by visiting my <nuxt-link to="/about">About</nuxt-link> page.
      <v-spacer></v-spacer>
      There, I provide a brief summary about my life.
      <v-spacer></v-spacer>
      Additionally, my CV is also available on my website. By clicking the button, you can review my CV and learn more about me.
      <v-spacer></v-spacer>
      </h3>
      <br>
      </v-card>
  </v-card>

</template>

<script>
  export default {
    data: () => ({
    }),
  }
</script>

<style>

</style>