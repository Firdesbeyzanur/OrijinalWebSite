<template>
    <v-card
      class="mx-auto"
    >
  
      <v-toolbar
        color="indigo"
        dark
      >
  
        <v-toolbar-title>Discover</v-toolbar-title>
  
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
              <v-card-title class="text-align: start;" @click="goPage(card.link)">{{ card.title }}</v-card-title>
                </v-btn>
                <v-btn icon>
                  <v-icon @click="goPage(card.link)">{{ card.icon }}</v-icon>
                </v-btn>

              </v-card-actions>
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
      { title: 'Find the Hulk', src: 'https://user-images.githubusercontent.com/99497565/230842395-0a023558-2739-4ca2-bf8d-464fe74a1a59.jpg', icon: 'mdi-cat' , link: 'https://github.com/Firdesbeyzanur/Hulku-Bul' , flex: 4  },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/206258611-c4233670-817f-4025-8e63-3beabc6a7691.jpg', icon: 'mdi-movie' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/206262912-586b0abc-7d4e-42ef-bf77-d11342509b05.jpg', icon: 'mdi-arrange-send-to-back' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/230846792-f10645aa-54a6-4fff-a6de-ccbe5ebfe13c.jpg', icon: 'mdi-arrange-bring-forward' ,  link: 'https://github.com/Firdesbeyzanur/Card-App-1' ,flex: 4 },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/206264529-155bbece-1469-4c26-8cb4-3ce8a7ca76cc.jpg', icon: 'mdi-arrange-bring-to-front' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Card App', src: 'https://user-images.githubusercontent.com/99497565/230847129-3817d1df-d598-498a-87af-6c555c0db3b4.jpg', icon: 'mdi-mushroom' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Form List', src: 'https://user-images.githubusercontent.com/99497565/206272893-8534f15c-12ea-4a6f-8bcb-e11668d6d1ae.jpg', icon: 'mdi-account-key' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Website', src: 'https://user-images.githubusercontent.com/99497565/230848352-5c5a9338-c513-4658-b158-390c98f82bc3.jpg', icon: 'mdi-ghost' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'My Application', src: 'https://user-images.githubusercontent.com/99497565/214500850-03d82613-6753-4cb5-b11d-f6cfc10e1f22.png', icon: 'mdi-airballoon' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Number App', src: 'https://user-images.githubusercontent.com/99497565/214502434-af50d127-ced2-4d04-a3fb-6141b0cc4081.png', icon: 'mdi-code-equal' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Note Application', src: 'https://user-images.githubusercontent.com/99497565/230848792-39b2f160-4517-4c42-8a28-2054c87600e9.jpg', icon: 'mdi-clipboard-check' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Blog', src: 'https://user-images.githubusercontent.com/99497565/220835798-f5cb63dd-fdc8-4334-a919-3b77dd2bc87b.png', icon: 'mdi-gmail' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'CarTrader', src: 'https://user-images.githubusercontent.com/99497565/223665669-4e28bdd7-ee93-409b-8d08-d0420062a6f5.png', icon: 'mdi-car' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Food Blog', src: 'https://user-images.githubusercontent.com/99497565/226338846-60426fb2-4e94-453f-9ca2-d486254971a2.png', icon: 'mdi-food' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
      { title: 'Cryptocurrency', src: 'https://user-images.githubusercontent.com/99497565/230595933-94a87738-97df-4f3a-911b-0f3b1795c916.png', icon: 'mdi-chart-line' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , flex: 4 },
    ],
  }),
  methods: {
    goPage: function (link) {
      window.open(link, '_blank');
    }
  }
}
</script>