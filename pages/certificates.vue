<template>
    <v-card
      class="mx-auto"
    >
  
      <v-toolbar
        dark
      >
  
        <v-toolbar-title>Projects</v-toolbar-title>
  
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
              <br>
              <v-dialog
                v-model="dialog"
                persistent
                max-width="290"
              >
                <template v-slot:activator="{ on, attrs }" >
                  <v-btn
                    dark
                    v-bind="attrs"
                    v-on="on"
                    v-for="card in cards"
                :key="card.title"
                :cols="card.flex"
                :icon="card.icon"
                  >
                  <v-icon> mdi-book </v-icon> 
                  {{ card.title }}
                  </v-btn>
                </template>
                <v-card >

                  <v-card-title class="text-h5">
                    {{ card.title }}
                  </v-card-title>
                  <v-card-text>Let Google help apps determine location. This means sending anonymous location data to Google, even when no             apps are running.</v-card-text>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                      color="red darken-1"
                      text
                      @click="dialog = false"
                    >
                      Cancel
                    </v-btn>
                    <v-btn
                      color="green darken-1"
                      text
                      @click="dialog = false"
                    >
                      OK
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
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
    ],
    dialog: false,
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