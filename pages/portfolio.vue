<template>
    <v-card
      class="mx-auto"
    >
  
      <v-toolbar
        dark
      >
  
        <v-toolbar-title>Project</v-toolbar-title>
  
        <v-spacer></v-spacer>

      </v-toolbar>
  
      <v-container fluid>
        <v-row dense>
          <v-col
            v-for="card in cards"
            :key="card.title"
            :cols="card.flex"
            :icon="card.icon"
          >
            <v-card>
              <v-img
                :src="card.src"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="300px"
                >
              </v-img>
  

              <v-card-actions>
                <v-btn>
              <h4 class="text-align: start; text-size: 15px" @click="goPage(card.link)"><v-icon> mdi-link-variant </v-icon> {{ card.title }} </h4>
                </v-btn>
                <v-btn icon>
                  <v-icon 
                  @click="toggleShow(card)">{{ card.icon }}</v-icon>
                </v-btn>

              </v-card-actions>
                <v-expand-transition>
                  <div v-show="card.show">
                    <v-divider></v-divider>
                    <v-card-text>
                      {{ card.text }}
                    </v-card-text>
                 </div>
                </v-expand-transition>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </template>

<script>

export default {
  
  data: () => ({
    cards: [
      { title: 'Cryptocurrency', src: 'https://user-images.githubusercontent.com/99497565/231105012-fdd76a6d-bbf8-4278-b8ae-fe5beb1c48bc.jpg', icon: 'mdi-chart-line' , link: 'https://github.com/Firdesbeyzanur/Cryptocurrency' , text: 'Cryptocurrency exchange tracking in a table with information pulled from the API.' , flex: 4 , show: false },
      { title: 'Food Blog', src: 'https://cdn-prod.medicalnewstoday.com/content/images/articles/317/317257/cupcakes.jpg', icon: 'mdi-food' , link: 'https://github.com/Firdesbeyzanur/Food-App' , text: 'A blog with dessert recipes.' , flex: 4 , show: false },
      { title: 'CarTrader', src: 'https://hips.hearstapps.com/hmg-prod/images/2023-mclaren-artura-101-1655218102.jpg?crop=1.00xw:0.847xh;0,0.153xh&resize=1200:*', icon: 'mdi-car' , link: 'https://github.com/Firdesbeyzanur/CarTrader' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 4 , show: false },
      { title: 'Find the Hulk', src: 'https://cat-world.com/wp-content/uploads/2017/03/all-about-white-cats.jpg', icon: 'mdi-cat' , link: 'https://github.com/Firdesbeyzanur/Hulku-Bul' , text: 'It\'s a sticky memory game for my cat. Guess what\'s on the face-down card.' , flex: 4 , show: false  },
      { title: 'Website', src: 'https://user-images.githubusercontent.com/99497565/231108842-84284848-d968-46e9-92a1-b7e0f07e11d4.jpg', icon: 'mdi-ghost' , link: 'https://github.com/Firdesbeyzanur/Nuxtjs-WebSite' , text: 'My first mini website I made using Nuxt.' , flex: 4 , show: false },
      { title: 'My Application', src: 'https://images.pexels.com/photos/270408/pexels-photo-270408.jpeg?auto=compress&cs=tinysrgb&w=600', icon: 'mdi-airballoon' , link: 'https://github.com/Firdesbeyzanur/Vue3-Pictures' , text: 'An app to upload and delete photos.' , flex: 4 , show: false },
      { title: 'Note Application', src: 'https://leverageedublog.s3.ap-south-1.amazonaws.com/blog/wp-content/uploads/2020/01/24220440/How-to-Write-a-Leave-Application-.png', icon: 'mdi-clipboard-check' , link: 'https://github.com/Firdesbeyzanur/FireBase-NotesApp' , text: 'Do you forget things to do during the day? Then this note app is for you.' , flex: 4 , show: false },
      { title: 'Form List', src: 'https://cdn.dribbble.com/users/300847/screenshots/16084243/media/29293a025ee2ce762cc260bcf7f1db08.png?compress=1&resize=400x300', icon: 'mdi-account-key' , link: 'https://github.com/Firdesbeyzanur/Form' , text: 'Form application. Enter your information, click on the button and your information will come back on the card.' , flex: 4 , show: false },
      { title: 'Number App', src: 'https://cdn.dribbble.com/users/1872109/screenshots/15301249/media/0247608b79cc452812e74925dc295bec.jpg?compress=1&resize=400x300', icon: 'mdi-code-equal' , link: 'https://github.com/Firdesbeyzanur/Nuxt-RandomNumber' , text: 'An application to generate random comma and whole numbers.' , flex: 4 , show: false },
      { title: 'Blog', src: 'https://birhost.net/wp-content/uploads/2021/12/en-iyi-blog-siteleri-1.webp', icon: 'mdi-gmail' , link: 'https://github.com/Firdesbeyzanur/WebSite' , text: 'I was asked for a blog page. A blog with a login page and admin login.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://cdn.dribbble.com/users/4208985/screenshots/14980117/media/75fabfb042600459c814b2b832c449a7.png?compress=1&resize=400x300', icon: 'mdi-mushroom' , link: 'https://github.com/Firdesbeyzanur/Card-App-4' , text: 'A card app with additional features in the edit section with description section and change image section.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://assets.materialup.com/uploads/856811ea-9319-4505-8745-b33d1c7319e3/material-design-cards.jpg', icon: 'mdi-arrange-bring-forward' ,  link: 'https://github.com/Firdesbeyzanur/Card-App-3' , text: 'A card app with a description section and an edit section.' ,flex: 4 , show: false },
      { title: 'Card App', src: 'https://camo.githubusercontent.com/a465785c162542c7b0ca85d03a9dc30b15992046f169132b9614f6d9cf4adfa7/687474703a2f2f692e696d6775722e636f6d2f6944796d3762492e706e67', icon: 'mdi-arrange-send-to-back' , link: 'https://github.com/Firdesbeyzanur/AddImageCard' , text: 'An application where you can upload up to 10 pieces with pictures and enter your information.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://www.sketchappsources.com/resources/source-image/idcard-pink-floyd-material.png', icon: 'mdi-arrange-bring-to-front' , link: 'https://github.com/Firdesbeyzanur/Card-App-2' , text: 'Click on the pen to open the edit section and edit it.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://www.sketchappsources.com/resources/source-image/material-card-design-fazurrehman.png', icon: 'mdi-movie' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , text: 'Edit the information on the card however you like.' , flex: 4 , show: false },
    ],
  }),
  methods: {
    goPage: function (link) {
      window.open(link, '_blank');
    },
    toggleShow(card) {
      // Açıklamanın görünürlüğünü değiştirmek için kullanılabilir
      card.show = !card.show;
    }
  }
}
</script>