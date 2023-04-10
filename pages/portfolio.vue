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
              <v-card-title class="text-align: start;" @click="goPage(card.link)"><v-icon> mdi-link-variant </v-icon> {{ card.title }} </v-card-title>
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
      { title: 'Cryptocurrency', src: 'https://user-images.githubusercontent.com/99497565/230595933-94a87738-97df-4f3a-911b-0f3b1795c916.png', icon: 'mdi-chart-line' , link: 'https://github.com/Firdesbeyzanur/Cryptocurrency' , text: 'Cryptocurrency exchange tracking in a table with information pulled from the API.' , flex: 4 , show: false },
      { title: 'Food Blog', src: 'https://user-images.githubusercontent.com/99497565/226338846-60426fb2-4e94-453f-9ca2-d486254971a2.png', icon: 'mdi-food' , link: 'https://github.com/Firdesbeyzanur/Food-App' , text: 'A blog with dessert recipes.' , flex: 4 , show: false },
      { title: 'CarTrader', src: 'https://user-images.githubusercontent.com/99497565/223665669-4e28bdd7-ee93-409b-8d08-d0420062a6f5.png', icon: 'mdi-car' , link: 'https://github.com/Firdesbeyzanur/CarTrader' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 4 , show: false },
      { title: 'Find the Hulk', src: 'https://user-images.githubusercontent.com/99497565/230842395-0a023558-2739-4ca2-bf8d-464fe74a1a59.jpg', icon: 'mdi-cat' , link: 'https://github.com/Firdesbeyzanur/Hulku-Bul' , text: 'It\'s a sticky memory game for my cat. Guess what\'s on the face-down card.' , flex: 4 , show: false  },
      { title: 'Website', src: 'https://user-images.githubusercontent.com/99497565/230848352-5c5a9338-c513-4658-b158-390c98f82bc3.jpg', icon: 'mdi-ghost' , link: 'https://github.com/Firdesbeyzanur/Nuxtjs-WebSite' , text: 'My first mini website I made using Nuxt.' , flex: 4 , show: false },
      { title: 'My Application', src: 'https://user-images.githubusercontent.com/99497565/214500850-03d82613-6753-4cb5-b11d-f6cfc10e1f22.png', icon: 'mdi-airballoon' , link: 'https://github.com/Firdesbeyzanur/Vue3-Pictures' , text: 'An app to upload and delete photos.' , flex: 4 , show: false },

      { title: 'Note Application', src: 'https://user-images.githubusercontent.com/99497565/230848792-39b2f160-4517-4c42-8a28-2054c87600e9.jpg', icon: 'mdi-clipboard-check' , link: 'https://github.com/Firdesbeyzanur/FireBase-NotesApp' , text: 'Do you forget things to do during the day? Then this note app is for you.' , flex: 4 , show: false },
      { title: 'Form List', src: 'https://user-images.githubusercontent.com/99497565/206272893-8534f15c-12ea-4a6f-8bcb-e11668d6d1ae.jpg', icon: 'mdi-account-key' , link: 'https://github.com/Firdesbeyzanur/Form' , text: 'Form application. Enter your information, click on the button and your information will come back on the card.' , flex: 4 , show: false },
      { title: 'Number App', src: 'https://user-images.githubusercontent.com/99497565/214502434-af50d127-ced2-4d04-a3fb-6141b0cc4081.png', icon: 'mdi-code-equal' , link: 'https://github.com/Firdesbeyzanur/Nuxt-RandomNumber' , text: 'An application to generate random comma and whole numbers.' , flex: 4 , show: false },
      { title: 'Blog', src: 'https://user-images.githubusercontent.com/99497565/220835798-f5cb63dd-fdc8-4334-a919-3b77dd2bc87b.png', icon: 'mdi-gmail' , link: 'https://github.com/Firdesbeyzanur/WebSite' , text: 'I was asked for a blog page. A blog with a login page and admin login.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/230847129-3817d1df-d598-498a-87af-6c555c0db3b4.jpg', icon: 'mdi-mushroom' , link: 'https://github.com/Firdesbeyzanur/Card-App-4' , text: 'A card app with additional features in the edit section with description section and change image section.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/230846792-f10645aa-54a6-4fff-a6de-ccbe5ebfe13c.jpg', icon: 'mdi-arrange-bring-forward' ,  link: 'https://github.com/Firdesbeyzanur/Card-App-3' , text: 'A card app with a description section and an edit section.' ,flex: 4 , show: false },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/206262912-586b0abc-7d4e-42ef-bf77-d11342509b05.jpg', icon: 'mdi-arrange-send-to-back' , link: 'https://github.com/Firdesbeyzanur/AddImageCard' , text: 'An application where you can upload up to 10 pieces with pictures and enter your information.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/206264529-155bbece-1469-4c26-8cb4-3ce8a7ca76cc.jpg', icon: 'mdi-arrange-bring-to-front' , link: 'https://github.com/Firdesbeyzanur/Card-App-2' , text: 'Click on the pen to open the edit section and edit it.' , flex: 4 , show: false },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/206258611-c4233670-817f-4025-8e63-3beabc6a7691.jpg', icon: 'mdi-movie' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , text: 'Edit the information on the card however you like.' , flex: 4 , show: false },
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