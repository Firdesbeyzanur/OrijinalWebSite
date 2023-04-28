<template>
    <v-card
      class="mx-auto"
    >
  
      <v-toolbar
        dark
      >
  
        <v-toolbar-title>Projects</v-toolbar-title>

        <v-spacer></v-spacer>
        
        <v-menu offset-y>
    <template #activator="{ on }">
      <v-btn v-on="on"
      color="blue-grey"
      rounded
      >
        Categories
      </v-btn>
    </template>

    <v-list>
      <v-list-item v-for="(category, index) in categories" :key="index" @click="filterProjects(category)">
        <v-list-item-title>
          {{ category }}
        </v-list-item-title>
      </v-list-item>
    </v-list>
  </v-menu>

      </v-toolbar>
      <v-spacer></v-spacer>
      <v-container fluid>
        <v-row dense>
          <v-col
            v-for="project in filteredProjects" :key="project.id"
            :title="project.title"
            :cols="project.flex"
            :icon="project.icon"
          >
            <v-card>
              <v-img
                :src="project.src"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="300px"
                >
              </v-img>
  

              <v-card-actions class="d-flex justify-right">
                <v-btn small>
              <h4 class=" button" @click="goPage(project.link)"><v-icon> mdi-link-variant </v-icon> {{ project.title }} </h4>
                </v-btn> 
                <v-btn icon>
                  <v-icon 
                  @click="toggleShow(project)">{{ project.icon }}</v-icon>
                </v-btn>

              </v-card-actions>
                <v-expand-transition>
                  <div v-show="project.show">
                    <v-divider></v-divider>
                    <v-card-text>
                      {{ project.text }}
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
    projects: [
      { title: 'Cryptocurrency', src: 'https://user-images.githubusercontent.com/99497565/231105012-fdd76a6d-bbf8-4278-b8ae-fe5beb1c48bc.jpg', icon: 'mdi-chart-line' , link: 'https://github.com/Firdesbeyzanur/Cryptocurrency' , text: 'Cryptocurrency exchange tracking in a table with information pulled from the API.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Food Blog', src: 'https://cdn-prod.medicalnewstoday.com/content/images/articles/317/317257/cupcakes.jpg', icon: 'mdi-food' , link: 'https://github.com/Firdesbeyzanur/Food-App' , text: 'A blog with dessert recipes.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'CarTrader', src: 'https://hips.hearstapps.com/hmg-prod/images/2023-mclaren-artura-101-1655218102.jpg?crop=1.00xw:0.847xh;0,0.153xh&resize=1200:*', icon: 'mdi-car' , link: 'https://github.com/Firdesbeyzanur/CarTrader' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Find the Hulk', src: 'https://cat-world.com/wp-content/uploads/2017/03/all-about-white-cats.jpg', icon: 'mdi-cat' , link: 'https://github.com/Firdesbeyzanur/Hulku-Bul' , text: 'It\'s a sticky memory game for my cat. Guess what\'s on the face-down card.' , flex: 4 , show: false, categories: ['Vue.js', 'All']  },
      { title: 'Website', src: 'https://user-images.githubusercontent.com/99497565/231368901-a661c382-c10a-4de5-9178-0926676e40bd.png', icon: 'mdi-ghost' , link: 'https://github.com/Firdesbeyzanur/Nuxtjs-WebSite' , text: 'My first mini website I made using Nuxt.' , flex: 4 , show: false, categories: ['Nuxt.js', 'All'] },
      { title: 'Unity Game', src: 'https://trthaberstatic.cdn.wp.trt.com.tr/resimler/1858000/oyun-sektoru-getty-1859699.jpg', icon: 'mdi-gamepad-variant' , link: 'https://github.com/Firdesbeyzanur/Survival-of-The-Fallen' , text: 'It is a thriller game that we developed with my team of 5 people, which I worked as a developer during the Oyun ve Uygulama Akademisi bootcamp process.' , flex: 4 , show: false, categories: ['Unity', 'All'] },
      { title: 'My Application', src: 'https://images.pexels.com/photos/270408/pexels-photo-270408.jpeg?auto=compress&cs=tinysrgb&w=600', icon: 'mdi-airballoon' , link: 'https://github.com/Firdesbeyzanur/Vue3-Pictures' , text: 'An app to upload and delete photos.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Note Application', src: 'https://leverageedublog.s3.ap-south-1.amazonaws.com/blog/wp-content/uploads/2020/01/24220440/How-to-Write-a-Leave-Application-.png', icon: 'mdi-clipboard-check' , link: 'https://github.com/Firdesbeyzanur/FireBase-NotesApp' , text: 'Do you forget things to do during the day? Then this note app is for you.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Form List', src: 'https://cdn.dribbble.com/users/300847/screenshots/16084243/media/29293a025ee2ce762cc260bcf7f1db08.png?compress=1&resize=400x300', icon: 'mdi-account-key' , link: 'https://github.com/Firdesbeyzanur/Form' , text: 'Form application. Enter your information, click on the button and your information will come back on the card.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Number App', src: 'https://cdn.dribbble.com/users/1872109/screenshots/15301249/media/0247608b79cc452812e74925dc295bec.jpg?compress=1&resize=400x300', icon: 'mdi-code-equal' , link: 'https://github.com/Firdesbeyzanur/Nuxt-RandomNumber' , text: 'An application to generate random comma and whole numbers.' , flex: 4 , show: false, categories: ['Nuxt.js', 'All'] },
      { title: 'Blog', src: 'https://birhost.net/wp-content/uploads/2021/12/en-iyi-blog-siteleri-1.webp', icon: 'mdi-gmail' , link: 'https://github.com/Firdesbeyzanur/WebSite' , text: 'I was asked for a blog page. A blog with a login page and admin login.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 1', src: 'https://cdn.dribbble.com/users/4208985/screenshots/14980117/media/75fabfb042600459c814b2b832c449a7.png?compress=1&resize=400x300', icon: 'mdi-newspaper' , link: 'https://github.com/Firdesbeyzanur/Card-App-4' , text: 'A card app with additional features in the edit section with description section and change image section.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 2', src: 'https://assets.materialup.com/uploads/856811ea-9319-4505-8745-b33d1c7319e3/material-design-cards.jpg', icon: 'mdi-arrange-bring-forward' ,  link: 'https://github.com/Firdesbeyzanur/Card-App-3' , text: 'A card app with a description section and an edit section.' ,flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 3', src: 'https://camo.githubusercontent.com/a465785c162542c7b0ca85d03a9dc30b15992046f169132b9614f6d9cf4adfa7/687474703a2f2f692e696d6775722e636f6d2f6944796d3762492e706e67', icon: 'mdi-arrange-send-to-back' , link: 'https://github.com/Firdesbeyzanur/AddImageCard' , text: 'An application where you can upload up to 10 pieces with pictures and enter your information.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 4', src: 'https://www.sketchappsources.com/resources/source-image/idcard-pink-floyd-material.png', icon: 'mdi-arrange-bring-to-front' , link: 'https://github.com/Firdesbeyzanur/Card-App-2' , text: 'Click on the pen to open the edit section and edit it.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 5', src: 'https://www.sketchappsources.com/resources/source-image/material-card-design-fazurrehman.png', icon: 'mdi-multiplication-box' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , text: 'Edit the information on the card however you like.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Titanic Dataset', src: 'https://upload.wikimedia.org/wikipedia/commons/f/fd/RMS_Titanic_3.jpg', icon: 'mdi-qqchat' , link: 'https://github.com/Firdesbeyzanur/TitanicDataset' , text: 'In the Titanic dataset, data preprocessing was performed, ExtraTressClassifier and Feature Importance were extracted, SelectKBest was scored, correlation maps were created, non-normally distributed data were standardized and basic statistical information was extracted.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Insurance Dataset', src: 'https://api.pitsasinsurances.com/dl/images/PITSAS%20ARTICLE%20-%20WHAT%20IS%20A%20QUOTE%20IN%20INSURANCE.jpg', icon: 'mdi-clipboard-plus' , link: 'https://github.com/Firdesbeyzanur/InsuranceDataset' , text: 'In the insurance dataset, prediction was performed with classifiers, Accuracy, Precision, Recall, F1-Score results were tabulated and confusion matrix was plotted.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Stock Dataset', src: 'https://caltech-prod.s3.amazonaws.com/main/images/CollinCamerer-ShortSelling-0.2e16d0ba.fill-1600x810-c100.jpg', icon: 'mdi-cash' , link: 'https://github.com/Firdesbeyzanur/StockDataset' , text: 'Time Series, Regression and LSTM analysis were performed on the stock market data set and ARIMA model was applied.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Forecast Process', src: 'https://www.bounteous.com/sites/default/files/styles/file_entity_browser_thumbnail/public/insights/2020-09/previews/20200902_blog_-forecasting-with-time-series-models-using-python_pt2_website.png?itok=ausSadlv', icon: 'mdi-account-convert' , link: 'https://github.com/Firdesbeyzanur/Tahminleme-Islemi' , text: 'Python code that predicts the age, race and gender of people after various operations.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Face Matching', src: 'https://img.freepik.com/premium-vector/woman-s-face-recognition-concept-biometric-face-scanning-futuristic-security-personal-verification-monitor-cyber-protection-concept_212168-585.jpg?w=2000', icon: 'mdi-account-circle' , link: 'https://github.com/Firdesbeyzanur/Yuz-Eslestirme' , text: 'Face matching of the people in the database was done using MATLAB.' , flex: 4 , show: false, categories: ['MATLAB', 'All'] },
      { title: 'Prediction', src: 'https://media.istockphoto.com/id/1195209543/vector/facial-recognition-system-with-woman-face-flat-vector-illustration-isolated.jpg?s=612x612&w=0&k=20&c=SzxSs3gXdLQAVlt67oNRW1uw9V3T6-e6EokxZN-jSWk=', icon: 'mdi-account-multiple' , link: 'https://github.com/Firdesbeyzanur/Prediction-Classification' , text: 'A program that predicts people\'s age, gender and ethnicity with Python' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Mushroom Class', src: 'https://i.ytimg.com/vi/tQZyurzh5Ms/maxresdefault.jpg', icon: 'mdi-mushroom' , link: 'https://github.com/Firdesbeyzanur/Mushroom-classification' , text: 'In this project, we will use the "Mushroom Classification" dataset, a public dataset from kaggle.com, and try to figure out whether a mushroom is edible or not.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Insurance Dataset', src: 'https://miro.medium.com/v2/resize:fit:1400/0*yRhQ28Nd53cTSCR6', icon: 'mdi-clipboard-account' , link: 'https://github.com/Firdesbeyzanur/GlobalAIHub-Project' , text: 'The insurance dataset was examined at the bootcamp organized by Global AI Hub.' , flex: 4 , show: false, categories: ['Python', 'All']},
      { title: 'Date Fruit Dataset', src: 'https://storage.googleapis.com/kaggle-datasets-images/2049845/3400552/7ea4cce54ee9f92170cf7e4dfcb72394/dataset-card.jpg?t=2022-04-03-09-30-05', icon: 'mdi-food-apple' , link: 'https://github.com/Firdesbeyzanur/Deep-Learning' , text: 'We created a neural network to classify dates with TensorFlow. For this, we used the "Date Fruit Dataset" available on Kaggle.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Image Classification', src: 'https://miro.medium.com/v2/resize:fit:1400/0*gPfifkgrc7UIjZEA', icon: 'mdi-grid' , link: 'https://github.com/Firdesbeyzanur/CNN' , text: 'In this project, we built a convolutional neural network to solve a multi-class image classification problem.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Movie Review Dataset', src: 'https://www.karel.com.tr/sites/default/files/pictures/ik-film-onerileri-a.jpg', icon: 'mdi-movie' , link: 'https://github.com/Firdesbeyzanur/Deep-Learning_2' , text: 'Recurrent neural networks. IMDB Movie Review Dataset was used.' , flex: 4 , show: false, categories: ['Python', 'All']},
      { title: 'Lena512 Puzzle', src: 'https://images.wallpaperscraft.com/image/single/puzzles_puzzle_part_106469_2780x2780.jpg', icon: 'mdi-puzzle' , link: 'https://github.com/Firdesbeyzanur/Lena512Disassembly' , text: 'Lena512 image split into 4 parts with MATLAB.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Lena512 Frame', src: 'https://img.rawpixel.com/s3fs-private/rawpixel_images/website_content/v695-taus-20-abstractgradientbackground2_1.jpg?w=800&dpr=1&fit=default&crop=default&q=65&vib=3&con=3&usm=15&bg=F4F4F3&ixlib=js-2.2.1&s=42cdcbcbb4eb13ce76b92984d6f53da7', icon: 'mdi-image-filter-frames' , link: 'https://github.com/Firdesbeyzanur/Lena512Frame' , text: 'We have the Lena512 picture in a black frame.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Lena512 Round Frame', src: 'https://img.freepik.com/premium-vector/silver-glitter-frame-circle-frame-with-shiny-sparkles-dark-transparent-background-vector-illustration_515038-5322.jpg?w=2000', icon: 'mdi-checkbox-blank-circle' , link: 'https://github.com/Firdesbeyzanur/Lena512RoundFrame' , text: 'We have enclosed the Lena512 picture in a black round frame.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Lena512 Resolution', src: 'https://hullabaloo.co.uk/wp-content/uploads/2016/03/Hullabaloo-Loughborough-Graphics-Design-Blog-Images-0042..jpg', icon: 'mdi-file-image' , link: 'https://github.com/Firdesbeyzanur/Lena512Resolution' , text: 'We have output the Lena512 image in different resolutions.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Xray Image', src: 'https://www.e7health.com/files/blogs/chest-x-ray-29.jpg', icon: 'mdi-hospital' , link: 'https://github.com/Firdesbeyzanur/XrayImageLesion' , text: 'The negative of the xray image was taken, the lesion was circled, spanned in the gray level range of 0.5-0.75, and the negative and gray level range were combined. ' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Histogram', src: 'https://www.shutterbug.com/images/styles/600_wide/public/promoh61617.png', icon: 'mdi-chart-histogram' , link: 'https://github.com/Firdesbeyzanur/Histogram' , text: 'We got the input and output histogram images of the image. ' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
    ],
    categories: [ 'All', 'Unity', 'Python', 'Vue.js', 'Nuxt.js', 'MATLAB' ],
    selectedCategory: null
  }),
  computed: {
      filteredProjects() {
        if (!this.selectedCategory) {
          return this.projects;
        }
        return this.projects.filter(project => project.categories.includes(this.selectedCategory));
      }
    },
  methods: {
    goPage: function (link) {
      window.open(link, '_blank');
    },
    toggleShow(project) {
      project.show = !project.show;
    },
    filterProjects(category) {
        this.selectedCategory = category;
      },
  }
}
</script>

<style scoped>
.my-btn {
  margin-right: 8px;
  transition: all 0.2s ease-in-out;

}
.my-btn:hover {
  transform: scale(1.1);
}
.button {
  margin-right: 8px;
}
.button {
  margin-right: 8px;
  color: #fff;
  transition: transform 0.3s ease;
}

.button:hover {
  transform: rotate(360deg);
}


</style>