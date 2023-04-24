<template>
  <v-card
    class="mx-auto"
  >

    <v-toolbar
      dark
    >

      <v-toolbar-title>Certificates</v-toolbar-title>

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
              height="420px"
              >
            </v-img>
            <v-card-actions>
              <v-btn>
                <h4 class="text-align: start; text-size: 15px" @click="goCertificates(card.link)"><v-icon> mdi-link-variant </v-icon> {{ card.title }} </h4>
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
    { title: 'Vue.Js', src: 'https://www.freecodecamp.org/news/content/images/size/w2000/2022/08/Vue-Blog-Cover-2.png', icon: 'mdi-certificate' , link: 'VueJsEng.pdf' , text: 'This is the course certificate I received about Vue.Js from the Udemy platform. (English)' , flex: 6 , show: false },
    { title: 'Vue.Js', src: 'https://miro.medium.com/max/6416/1*7OCwu--TWqVluPMsZdzWKw.png', icon: 'mdi-certificate' , link: 'VueJsTR.pdf' , text: 'This is the course certificate I received about Vue.Js from the Udemy platform. (Turkish)' , flex: 6 , show: false },
    { title: 'Nuxt.Js 2', src: 'https://blog.logrocket.com/wp-content/uploads/2020/11/nuxt-js-component-testing.png', icon: 'mdi-certificate' , link: 'NuxtJs2.pdf' , text: 'This is the course certificate I received from Udemy platform about Nuxt.Js 2. (English)' , flex: 6 , show: false },
    { title: 'Nuxt.Js 3', src: 'https://nuxtjs.org/_nuxt/image/0fc764.png', icon: 'mdi-certificate' , link: 'NuxtJs3.pdf' , text: 'This is the course certificate I received from Udemy platform about Nuxt.Js 3. (English)' , flex: 6 , show: false },
    { title: 'Nesneye Dayali Programlama - C#', src: 'https://preview.redd.it/1920-x-1080-c-wallpaper-v0-nbc8i22ia3091.png?auto=webp&s=a8e86c23feadfaf1d4a2b88b2d9a19e5658c0c3b', icon: 'mdi-certificate' , link: 'NesneyeDayaliProgramlama-CSharpGelistirmeveUyumEgitimi.pdf' , text: 'I earned a certificate from the Object-Oriented Programming - C# Development and Implementation Training program that I attended at Altıeylül Public Education Center. Throughout this training process, I gained extensive knowledge in C# programming language and object-oriented programming. I applied this knowledge by developing projects in real-world scenarios, which made me even more proficient in the C# programming language. The certificate I received will play a significant role in my personal development and future career goals.' , flex: 6 , show: false },
    { title: 'C++ Programlama Gelistirme', src: 'https://www.bilgiyazan.com.tr/wp-content/uploads/2017/11/BilgiYazan-Cpp-E%C4%9Fitimi.jpg', icon: 'mdi-certificate' , link: 'C++ProgramlamaGelistirmeveUyumEgitimi.pdf' , text: 'I earned a certificate from the C++ Programming Development and Adaptation Training program that I attended at Altıeylül Public Education Center. Throughout this training process, I gained extensive knowledge in C# programming language and object-oriented programming. I applied this knowledge by developing projects in real-world scenarios, which made me even more proficient in the C# programming language. The certificate I received will play a significant role in my personal development and future career goals.' , flex: 6 , show: false },
    { title: 'Python', src: 'https://www.filepicker.io/api/file/BFMMlbcQvml9HSqXcvNp', icon: 'mdi-certificate' , link: 'Python.pdf' , text: 'This is my course certificate for Python on the Udemy platform.' , flex: 6 , show: false },
    { title: 'Back-End with Python Bootcamp', src: 'https://user-images.githubusercontent.com/99497565/233932449-8885b6b4-699f-473d-a48d-89aaa8707f93.jpg', icon: 'mdi-certificate' , link: 'Back-EndwithPythonBootcamp.pdf' , text: 'I participated in the 5-week Back-End with Python Bootcamp organized by Techcareer and earned a certificate by completing a project. Throughout this training process, I gained extensive knowledge in back-end development with Python and applied this knowledge to develop real-world projects. Ultimately, the certificate I received was a valuable personal and professional achievement for me, and it will play a significant role in my future career goals.' , flex: 6 , show: false },
    { title: 'Unity ile Oyun Gelistirme', src: 'https://www.hubogi.com/wp-content/uploads/2021/08/Saving-Data-In-Unity-PlayerPrefs.jpg', icon: 'mdi-certificate' , link: 'UnityileOyunGelistirme.pdf' , text: 'I earned a certificate for successfully completing the Unity training offered by the Oyun ve Uygulama Akademisi, where I served as a developer on a 5-person team and designed a game during the bootcamp. Throughout the training process, I gained extensive knowledge in Unity game development and applied this knowledge to develop a game with my team. This certificate is a valuable recognition of my skills and accomplishments as a Unity developer, and I am proud to have earned it through the bootcamp.' , flex: 6 , show: false },
    { title: 'Teknoloji Girisimciliği', src: 'https://ustagirisimci.com/wp-content/uploads/2018/06/akillara-durgunluk-veren-8-teknolojik-girisim.jpg', icon: 'mdi-certificate' , link: 'TeknolojiGirisimciligi.pdf' , text: 'I participated in the entrepreneurship and technology education organized by Oyun ve Uygulama Akademisi and successfully completed it. During these trainings, I gained comprehensive knowledge in entrepreneurship and technology. At the end of the trainings, I earned a certificate, which is a valuable recognition of my skills and achievements. This certificate is an important reference for my knowledge and application skills in the fields of entrepreneurship and technology.' , flex: 6 , show: false },

    { title: 'AI Summer Camp', src: 'https://haber.sol.org.tr/sites/default/files/styles/content_image_size_type4/public/images/content/article/2022/02/23/global%20al%20hub.jpg?itok=mKIM_8d-', icon: 'mdi-certificate' , link: 'AISummerCamp.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Introduction to Deep Learning', src: 'https://www.mouser.com/blog/Portals/11/Dongang_Machine%20Learning_Theme%20Image-min_1.jpg', icon: 'mdi-certificate' , link: 'IntroductiontoDeepLearning.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Introduction to Machine Learning', src: 'https://miro.medium.com/v2/resize:fit:1400/1*cG6U1qstYDijh9bPL42e-Q.jpeg', icon: 'mdi-certificate' , link: 'IntroductiontoMachineLearning.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Makine Öğrenmesine Giris', src: 'https://s40424.pcdn.co/in/wp-content/uploads/2023/03/types-of-machine-learning.jpg.optimal.jpg', icon: 'mdi-certificate' , link: 'MakineÖğrenmesineGiris.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Python for Machine Learning', src: 'https://veriakademi.com/images/machine-learning-ogrenmek-istiyorum.png', icon: 'mdi-certificate' , link: 'PythonforMachineLearning.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Introduction to Python', src: 'https://statinfer.com/wp-content/uploads/intro_python_8.png', icon: 'mdi-certificate' , link: 'IntroductiontoPython.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'YetGen 21. Yüzyil Yetkinlikleri Eğitimi', src: 'https://d1fdloi71mui9q.cloudfront.net/HshVQG41R666UBV7aYa5_xP0Tg5JLLWBeZGPd', icon: 'mdi-certificate' , link: 'YetGen.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Google Proje Yonetimi', src: 'https://i.ndtvimg.com/i/2017-08/google-logo-reuters-650_650x400_71502168921.jpg?ver-20230421.111' , icon: 'mdi-certificate' , link: 'GoogleProjeYonetimi.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Proje Yonetiminin Temelleri', src: 'https://akademi.bilgeadam.com/wp-content/uploads/2021/11/Proje-Yonetiminin-Temelleri.jpg' , icon: 'mdi-certificate' , link: 'ProjeYonetimininTemelleri.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Projeyi Baslatma', src: 'https://miro.medium.com/max/1400/0*u5WGQxs1O2_p2k2d.png', icon: 'mdi-certificate' , link: 'ProjeyiBaslatmaProjeyeBasariylaAdimAtma.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Proje Planlamasi', src: 'https://www.esnaf724.com/dosyalar/yazi/1611133648.jpg', icon: 'mdi-certificate' , link: 'ProjePlanlamasiHerSeyiBirArayaGetirmek.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Projeyi Yurutme', src: 'https://www.datocms-assets.com/64859/1654170240-projeprogram01.jpg' , icon: 'mdi-certificate' , link: 'ProjeyiYurutmeProjeyiHayataGecirme.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Cevik Proje Yonetimi', src: 'https://miro.medium.com/v2/resize:fit:1024/1*nCZtpDlVGXHk0MpunGb0Sw.jpeg' , icon: 'mdi-certificate' , link: 'CevikProjeYonetimi.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'Bitirme Projesi', src: 'https://www.projectengineer.net/wp-content/uploads/2019/12/project-presentation-3.png' , icon: 'mdi-certificate' , link: 'BitirmeProjesiProjeYonetiminiGercekDunyada.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },
    { title: 'Versiyon Kontrolleri: Git ve GitHub', src: 'https://ciberninjas.com/wp-content/uploads/2019/12/git-github.webp', icon: 'mdi-certificate' , link: 'Git-GitHub.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },

    { title: 'HTML5 ile Web Gelistirme', src: 'https://www.qwerty-design.co.uk/wp-content/uploads/2012/11/html5-logo-750x440.png', icon: 'mdi-certificate' , link: 'HTML5.pdf' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 6 , show: false },
  ],
}),
methods: {
  goCertificates: function (link) {
    window.open(link, '_blank');
  },
  toggleShow(card) {
    card.show = !card.show;
  }
}
}
</script>