<template>
  <v-card
    class="mx-auto"
  >

    <v-toolbar
      dark
    >
      <v-toolbar-title>Certificates</v-toolbar-title>

      <v-spacer></v-spacer>
      <v-menu offset-y>
    <template #activator="{ on }">
      <v-btn v-on="on">
        Kategoriler
      </v-btn>
    </template>

    <v-list>
      <v-list-item v-for="(category, index) in categories" :key="index" @click="filterCertificates(category)">
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
          v-for="certificate in filteredCertificates" :key="certificate.id"
          :title="certificate.title"
          :cols="certificate.flex"
          :icon="certificate.icon"
        >
          <v-card>
            <v-img
              :src="certificate.src"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="420px"
              >
            </v-img>
            <v-card-actions>
              <v-btn>
                <h4 class="text-align: start; text-size: 15px" @click="goCertificates(certificate.link)"><v-icon> mdi-link-variant </v-icon> {{ certificate.title }} </h4>
              </v-btn>
              <v-btn icon>
                  <v-icon 
                  @click="toggleShow(certificate)">{{ certificate.icon }}</v-icon>
                </v-btn>
              </v-card-actions>
              <v-expand-transition>
                <div v-show="certificate.show">
                  <v-divider></v-divider>
                  <v-card-text>
                    {{ certificate.text }}
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
  certificates: [
    { title: 'Vue.Js', src: 'https://www.freecodecamp.org/news/content/images/size/w2000/2022/08/Vue-Blog-Cover-2.png', icon: 'mdi-certificate' , link: 'VueJsEng.pdf' , text: 'This is the course certificate I received about Vue.Js from the Udemy platform. (English)' , flex: 6 , show: false, categories: ['Udemy', 'All'] },
    { title: 'Vue.Js', src: 'https://miro.medium.com/max/6416/1*7OCwu--TWqVluPMsZdzWKw.png', icon: 'mdi-certificate' , link: 'VueJsTR.pdf' , text: 'This is the course certificate I received about Vue.Js from the Udemy platform. (Turkish)' , flex: 6 , show: false, categories: ['Udemy', 'All'] },
    { title: 'Nuxt.Js 2', src: 'https://blog.logrocket.com/wp-content/uploads/2020/11/nuxt-js-component-testing.png', icon: 'mdi-certificate' , link: 'NuxtJs2.pdf' , text: 'This is the course certificate I received from Udemy platform about Nuxt.Js 2. (English)' , flex: 6 , show: false, categories: ['Udemy', 'All'] },
    { title: 'Nuxt.Js 3', src: 'https://nuxtjs.org/_nuxt/image/0fc764.png', icon: 'mdi-certificate' , link: 'NuxtJs3.pdf' , text: 'This is the course certificate I received from Udemy platform about Nuxt.Js 3. (English)' , flex: 6 , show: false, categories: ['Udemy', 'All'] },
    { title: 'Nesneye Dayali Programlama - C#', src: 'https://preview.redd.it/1920-x-1080-c-wallpaper-v0-nbc8i22ia3091.png?auto=webp&s=a8e86c23feadfaf1d4a2b88b2d9a19e5658c0c3b', icon: 'mdi-certificate' , link: 'NesneyeDayaliProgramlama-CSharpGelistirmeveUyumEgitimi.pdf' , text: 'I earned a certificate from the Object-Oriented Programming - C# Development and Implementation Training program that I attended at Altıeylül Public Education Center. Throughout this training process, I gained extensive knowledge in C# programming language and object-oriented programming. I applied this knowledge by developing projects in real-world scenarios, which made me even more proficient in the C# programming language. The certificate I received will play a significant role in my personal development and future career goals.' , flex: 6 , show: false, categories: ['Halk Eğitim', 'All'] },
    { title: 'C++ Programlama Gelistirme', src: 'https://www.bilgiyazan.com.tr/wp-content/uploads/2017/11/BilgiYazan-Cpp-E%C4%9Fitimi.jpg', icon: 'mdi-certificate' , link: 'C++ProgramlamaGelistirmeveUyumEgitimi.pdf' , text: 'I earned a certificate from the C++ Programming Development and Adaptation Training program that I attended at Altıeylül Public Education Center. Throughout this training process, I gained extensive knowledge in C# programming language and object-oriented programming. I applied this knowledge by developing projects in real-world scenarios, which made me even more proficient in the C# programming language. The certificate I received will play a significant role in my personal development and future career goals.' , flex: 6 , show: false, categories: ['Halk Eğitim', 'All'] },
    { title: 'Python', src: 'https://www.filepicker.io/api/file/BFMMlbcQvml9HSqXcvNp', icon: 'mdi-certificate' , link: 'Python.pdf' , text: 'This is my course certificate for Python on the Udemy platform.' , flex: 6 , show: false, categories: ['Udemy', 'All'] },
    { title: 'Back-End with Python Bootcamp', src: 'https://user-images.githubusercontent.com/99497565/233932449-8885b6b4-699f-473d-a48d-89aaa8707f93.jpg', icon: 'mdi-certificate' , link: 'Back-EndwithPythonBootcamp.pdf' , text: 'I participated in the 5-week Back-End with Python Bootcamp organized by Techcareer and earned a certificate by completing a project. Throughout this training process, I gained extensive knowledge in back-end development with Python and applied this knowledge to develop real-world projects. Ultimately, the certificate I received was a valuable personal and professional achievement for me, and it will play a significant role in my future career goals.' , flex: 6 , show: false, categories: ['Techcareer', 'All'] },
    { title: 'Unity ile Oyun Gelistirme', src: 'https://www.hubogi.com/wp-content/uploads/2021/08/Saving-Data-In-Unity-PlayerPrefs.jpg', icon: 'mdi-certificate' , link: 'UnityileOyunGelistirme.pdf' , text: 'I earned a certificate for successfully completing the Unity training offered by the Oyun ve Uygulama Akademisi, where I served as a developer on a 5-person team and designed a game during the bootcamp. Throughout the training process, I gained extensive knowledge in Unity game development and applied this knowledge to develop a game with my team. This certificate is a valuable recognition of my skills and accomplishments as a Unity developer, and I am proud to have earned it through the bootcamp.' , flex: 6 , show: false, categories: ['Oyun ve Uygulama Akademisi', 'All'] },
    { title: 'Teknoloji Girisimciliği', src: 'https://ustagirisimci.com/wp-content/uploads/2018/06/akillara-durgunluk-veren-8-teknolojik-girisim.jpg', icon: 'mdi-certificate' , link: 'TeknolojiGirisimciligi.pdf' , text: 'I participated in the entrepreneurship and technology education organized by Oyun ve Uygulama Akademisi and successfully completed it. During these trainings, I gained comprehensive knowledge in entrepreneurship and technology. At the end of the trainings, I earned a certificate, which is a valuable recognition of my skills and achievements. This certificate is an important reference for my knowledge and application skills in the fields of entrepreneurship and technology.' , flex: 6 , show: false, categories: ['Oyun ve Uygulama Akademisi', 'All'] },
    { title: 'AI Summer Camp', src: 'https://haber.sol.org.tr/sites/default/files/styles/content_image_size_type4/public/images/content/article/2022/02/23/global%20al%20hub.jpg?itok=mKIM_8d-', icon: 'mdi-certificate' , link: 'AISummerCamp.pdf' , text: 'I attended trainings on machine learning with Python during the camp organized by Global AI Hub. During the trainings, we learned the basics of machine learning and then delved into more in-depth topics and performed various applications. In addition, we covered topics such as data preprocessing, model selection, and hyperparameter tuning. As a team, we worked on a real-life dataset for our final project and developed a machine learning model using that dataset. The success of the project was crucial in giving us the opportunity to apply what we learned during the trainings.' , flex: 6 , show: false, categories: ['Global AI Hub', 'All'] },
    { title: 'Introduction to Deep Learning', src: 'https://www.mouser.com/blog/Portals/11/Dongang_Machine%20Learning_Theme%20Image-min_1.jpg', icon: 'mdi-certificate' , link: 'IntroductiontoDeepLearning.pdf' , text: 'The deep learning camp organized by Global AI Hub was a very useful experience for me. The training I received on deep learning with Python programming language helped me learn the basic principles and workings of deep learning. During the training, I also had the opportunity to delve into in-depth topics and gain a better understanding of the concepts by working on real-life examples. The final project was one of the most exciting and beneficial parts of this camp. I had the opportunity to gain more knowledge about deep learning modeling in this project. ' , flex: 6 , show: false, categories: ['Global AI Hub', 'All'] },
    { title: 'Introduction to Machine Learning', src: 'https://miro.medium.com/v2/resize:fit:1400/1*cG6U1qstYDijh9bPL42e-Q.jpeg', icon: 'mdi-certificate' , link: 'IntroductiontoMachineLearning.pdf' , text: 'During this camp organized by Global AI Hub, I received training on machine learning. During the training, we learned the fundamentals of machine learning and then delved into more advanced topics and carried out applications. In addition, we covered topics such as data preprocessing, model selection, and hyperparameter tuning. In the final project, I worked on a real-life dataset and developed a machine learning model using this dataset.' , flex: 6 , show: false, categories: ['Global AI Hub', 'All'] },
    { title: 'Makine Öğrenmesine Giris', src: 'https://s40424.pcdn.co/in/wp-content/uploads/2023/03/types-of-machine-learning.jpg.optimal.jpg', icon: 'mdi-certificate' , link: 'MakineÖğrenmesineGiris.pdf' , text: 'As a result of the machine learning training provided by 10million.AI during this camp organized by Global AI Hub, I have earned this certificate. The training focused on the fundamentals of machine learning throughout its duration.' , flex: 6 , show: false, categories: ['Global AI Hub', 'All'] },
    { title: 'Python for Machine Learning', src: 'https://veriakademi.com/images/machine-learning-ogrenmek-istiyorum.png', icon: 'mdi-certificate' , link: 'PythonforMachineLearning.pdf' , text: 'I have earned this certificate by successfully completing the trainings available in the AI Business School.' , flex: 6 , show: false, categories: ['Global AI Hub', 'All'] },
    { title: 'Introduction to Python', src: 'https://statinfer.com/wp-content/uploads/intro_python_8.png', icon: 'mdi-certificate' , link: 'IntroductiontoPython.pdf' , text: 'I have earned this certificate by successfully completing the trainings available in the AI Business School.' , flex: 6 , show: false, categories: ['Global AI Hub', 'All'] },
    { title: 'YetGen 21. Yüzyil Yetkinlikleri Eğitimi', src: 'https://d1fdloi71mui9q.cloudfront.net/HshVQG41R666UBV7aYa5_xP0Tg5JLLWBeZGPd', icon: 'mdi-certificate' , link: 'YetGen.pdf' , text: 'I received training on 21st-century competencies from Yetkin Gençler (YetGen). The training included online courses on presentation techniques, Excel, and other similar topics. During the process, I also became a part of a large community and developed my communication skills. The training program provided by Yetkin Gençler (YetGen) has made me a more competent and prepared individual in the professional world. The courses taught practical skills necessary to meet the demands of the business world while also enabling me to communicate more effectively with my colleagues. As a part of the training program, the community we joined provided an environment where we could exchange ideas with each other. This allowed me to feel more comfortable interacting with others and express myself better. Through all of these experiences, I learned the skills necessary to be successful in the business world and developed myself in this field.' , flex: 6 , show: false, categories: ['YetGen', 'All'] },
    { title: 'Google Proje Yonetimi', src: 'https://i.ndtvimg.com/i/2017-08/google-logo-reuters-650_650x400_71502168921.jpg?ver-20230421.111' , icon: 'mdi-certificate' , link: 'GoogleProjeYonetimi.pdf' , text: 'As part of the training program of the Gaming and Application Academy, I participated in the Google Project Manager training on the Coursera platform and earned the certificate by successfully completing the tests. These trainings helped me gain practical skills in project management and enabled me to work more effectively in the processes of planning, implementation, and follow-up of projects. Additionally, these trainings made me feel more confident in project management in the business world and provided me with the opportunity to develop my skills in this area. Completion of these trainings offered by Google made me a more equipped individual in the professional world and can be considered an important step in achieving my career goals.' , flex: 6 , show: false, categories: ['Coursera', 'All'] },
    { title: 'Proje Yonetiminin Temelleri', src: 'https://akademi.bilgeadam.com/wp-content/uploads/2021/11/Proje-Yonetiminin-Temelleri.jpg' , icon: 'mdi-certificate' , link: 'ProjeYonetimininTemelleri.pdf' , text: 'I learned about the structure of the program, what project management is, what a project manager does, how I can use the skills I gained from my previous work experiences in project management positions, what types of project management positions I can take on after completing this course, and where I can find these positions.' , flex: 6 , show: false, categories: ['Coursera', 'All'] },
    { title: 'Projeyi Baslatma', src: 'https://miro.medium.com/max/1400/0*u5WGQxs1O2_p2k2d.png', icon: 'mdi-certificate' , link: 'ProjeyiBaslatmaProjeyeBasariylaAdimAtma.pdf' , text: 'In this course, I gained an understanding of the importance of the project initiation phase and learned about its key components, as well as how to determine the benefits and costs of projects.' , flex: 6 , show: false, categories: ['Coursera', 'All'] },
    { title: 'Proje Planlamasi', src: 'https://www.esnaf724.com/dosyalar/yazi/1611133648.jpg', icon: 'mdi-certificate' , link: 'ProjePlanlamasiHerSeyiBirArayaGetirmek.pdf' , text: 'I learned about the structure of the course, the benefits of planning, the key components of the planning phase, the difference between tasks and milestones, and how to identify milestones.' , flex: 6 , show: false, categories: ['Coursera', 'All'] },
    { title: 'Projeyi Yurutme', src: 'https://www.datocms-assets.com/64859/1654170240-projeprogram01.jpg' , icon: 'mdi-certificate' , link: 'ProjeyiYurutmeProjeyiHayataGecirme.pdf' , text: 'I learned about the structure of the course, what aspects of the project I need to track and how to do so. Additionally, I learned how to effectively manage changes, dependencies, and risks, and how to communicate critical risks to stakeholders.' , flex: 6 , show: false, categories: ['Coursera', 'All'] },
    { title: 'Cevik Proje Yonetimi', src: 'https://miro.medium.com/v2/resize:fit:1024/1*nCZtpDlVGXHk0MpunGb0Sw.jpeg' , icon: 'mdi-certificate' , link: 'CevikProjeYonetimi.pdf' , text: 'We examined the history, approach, and philosophy of Agile project management and Scrum theory in this course. In addition, I learned why Agile approaches are the best option for industries where change is prevalent and how to distinguish between different Agile approaches and how to use them together.' , flex: 6 , show: false, categories: ['Coursera', 'All'] },
    { title: 'Bitirme Projesi', src: 'https://www.projectengineer.net/wp-content/uploads/2019/12/project-presentation-3.png' , icon: 'mdi-certificate' , link: 'BitirmeProjesiProjeYonetiminiGercekDunyada.pdf' , text: 'I learned how to analyze project documents and supporting materials to determine project requirements, evaluate stakeholders, and solve problems encountered during the project. I learned how to complete a project initiation document and use it as a tool to bring stakeholders together on a common ground regarding the scope and objectives of the project. I learned how to make project objectives SMART by making them concrete and specific and using effective negotiation skills in communication with stakeholders to prioritize project objectives.' , flex: 6 , show: false, categories: ['Coursera', 'All'] },
    { title: 'Versiyon Kontrolleri: Git ve GitHub', src: 'https://ciberninjas.com/wp-content/uploads/2019/12/git-github.webp', icon: 'mdi-certificate' , link: 'Git-GitHub.pdf' , text: 'Thanks to this course on BTK Academy, I had the opportunity to learn common git commands used in software development process. Additionally, I learned how to track and collaborate on projects on GitHub using the git commands we learned. This enabled me to acquire the ability to work more effectively and efficiently in the software development process.' , flex: 6 , show: false, categories: ['BTK Akademi', 'All'] },
    { title: 'HTML5 ile Web Gelistirme', src: 'https://www.qwerty-design.co.uk/wp-content/uploads/2012/11/html5-logo-750x440.png', icon: 'mdi-certificate' , link: 'HTML5.pdf' , text: 'Thanks to the course I took at BTK Academy, I had the opportunity to learn the fundamentals of HTML5, the most commonly used markup language in web development, including its basic components, semantic structure, forms, and media elements. Additionally, I learned how to code in compliance with the latest standards of HTML5 and to enhance the accessibility of web pages. With these skills, I gained the ability to work more effectively and efficiently on web development projects.' , flex: 6 , show: false, categories: ['BTK Akademi', 'All'] },
  ],
  categories: [ 'All', 'Oyun ve Uygulama Akademisi', 'Coursera', 'Global AI Hub', 'Udemy', 'BTK Akademi', 'YetGen', 'Techcareer', 'Halk Eğitim' ],
    selectedCategory: null
}),
computed: {
  filteredCertificates() {
    if (!this.selectedCategory) {
      return this.certificates;
    }
    return this.certificates.filter(certificate => certificate.categories.includes(this.selectedCategory));
      }
  },
methods: {
  goCertificates: function (link) {
    window.open(link, '_blank');
  },
  toggleShow(certificate) {
    certificate.show = !certificate.show;
  },
  filterCertificates(category) {
        this.selectedCategory = category;
      },
}
}
</script>