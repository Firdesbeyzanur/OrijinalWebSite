<template>
    <div class="body">
  <h1 class="text-center">Welcome My Website</h1>
  <br>
    <v-carousel>
      <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="item.src"
        reverse-transition="fade-transition"
        transition="fade-transition"
      ></v-carousel-item>
    </v-carousel>
    <br><br>
    <v-card class="text-h6 ma-2 pa-2" color="#E6E6FA">
      <p class="text-center" style="color: black">Hello! I'm Firdes Beyzanur Şenocak, a Jr. Front-End Developer. 
        <br>
        Welcome to my website! You can learn more about me by visiting my <nuxt-link to="/about" style="color: #000080;">About Me </nuxt-link>page.
        <br>
        Above, you can see some images of the projects I have worked on. If you would like to see more of my projects and explore them, you can visit my <nuxt-link to="/portfolio" style="color: #333333;">Portfolio </nuxt-link>page. 
        <br>
        I'm here to provide you with an enjoyable experience. If you have any questions or need any help, please let me know!</p>
    </v-card>
  </div>
  </template>
  
  <script>
  export default {
    name: 'IndexPage',
    data () {
        return {
          items: [
            {
              src: 'https://user-images.githubusercontent.com/99497565/230596529-e74f965f-6e25-4bfc-a651-e7176f5000a2.png'
            },
            {
              src: 'https://user-images.githubusercontent.com/99497565/223665669-4e28bdd7-ee93-409b-8d08-d0420062a6f5.png'
            },
            {
              src: 'https://user-images.githubusercontent.com/99497565/230596974-5f757864-9569-4a06-ac20-7f1dfaeb4682.png'
            },
            {
              src: 'https://user-images.githubusercontent.com/99497565/230599002-fc2cdaa2-d9b6-4a7b-92c6-ea576efa66fa.png'
            },
            {
              src: 'https://user-images.githubusercontent.com/99497565/206253740-55782295-fee5-4e11-b7f8-a113b6eb1d4c.jpg'
            },
          ],
        }
      },
  }
  </script>

<style scoped>
.body {
    background-color: grey;
}
</style>
  