<template>
  <v-card
    class="mx-auto"
    max-width="1000px"
  >
    <v-img
      src="https://user-images.githubusercontent.com/99497565/231098768-60efb962-c429-45fb-a997-8f41b2607470.png"
      max-height="440px"
    >
    <v-btn 
      absolute
      dark
      bottom
      left
      color="#154360"
      >
      <v-icon> mdi-link-variant </v-icon> <a href="/firdes-beyzanur-senocak-cv.pdf" download="firdes-beyzanur-senocak.pdf" class="cvText">Click here for my CV</a>
    </v-btn>
  </v-img>

    <v-card-title>
      Jr. Front-End Developer
    </v-card-title>

    <v-card-actions>
      <v-btn
        color="orange lighten-2"
        text
        @click="show = !show"
      >
      For more information, please click here
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text class="homeText">
          Hello and Welcome!
          <v-spacer></v-spacer>
          I am Firdes Beyzanur Şenocak, and this is my personal website. I share my project contents here.
          <v-spacer></v-spacer>
          Welcome! I am Firdes Beyzanur Şenocak, and this is my personal website where I share content about my projects. I am here to share interesting topics, showcase my projects, and share my experiences with you. I hope you enjoy navigating through my site and feel free to contact me.
          <v-spacer></v-spacer>
          Thank you,
          <v-spacer></v-spacer>
          You can learn more about me by visiting my <nuxt-link to="/about">About Me</nuxt-link> page.
          There, I provide a brief summary about my life.
          <v-spacer></v-spacer>
          If you would like to review my projects, you can visit my <n-link to="portfolio">Portfolio</n-link> page. There, I showcase some of my own projects and provide detailed information about them.
          <v-spacer></v-spacer>
          If you would like to view my certificates, you can visit my <nuxt-link to="/certificates">Certificates</nuxt-link> page. There, you can find a list and details of various certificates I have earned. This page is a useful resource for those who want to learn more about the trainings I have taken and the skills I have acquired.
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
      show: false,
    }),
  }
</script>


<style scoped>
.homeText {
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: large;
}
.cvText {
  text-decoration: none;
  color: white;
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
</style>
