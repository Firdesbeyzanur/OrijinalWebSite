<template>
<div>
  <v-toolbar
        dark
      >
  
        <v-toolbar-title>About Me</v-toolbar-title>
  
        <v-spacer></v-spacer>

      </v-toolbar>

<v-timeline
    align-top
    :dense="$vuetify.breakpoint.smAndDown"
  >
    <v-timeline-item
      v-for="(item, i) in items"
      :key="i"
      :color="item.color"
      :icon="item.icon"
      :title="item.title"
      fill-dot
    >
      <v-card
        :color="item.color"
        class="ma-3 pa-3"

      >
        <v-card-title style="word-break: normal; color: black">          
          {{item.title}}
        </v-card-title>
      </v-card>
    </v-timeline-item>
  </v-timeline>
  
</div>
</template>

<script>
export default {
  name: 'about',
  data: () => ({
      items: [
        {
          title: 'I was born on May 19, 1996 in Erzincan.',
          color: '#a6caf0',
          icon: 'mdi-baby-buggy',
        },
        {
          title: 'I completed my primary, middle and high school education in Erzincan.',
          color: '#96d9af',
          icon: 'mdi-city',
        },
        {
          title: 'I won Balikesir University Electrical and Electronics Engineering and completed my undergraduate education in 2020 with an average of 3.04.',
          color: '#dac0de',
          icon: 'mdi-book-variant ',
        },
        {
          title: 'I continue my education life by doing my master\'s degree in Erzincan Binali Yildirim University Electrical and Electronics Engineering Department. I am at the thesis stage of my education. (My GPA is 4.00)',
          color: '#f8e7ad',
          icon: 'mdi-pencil',
        },
        {
          title: 'I am currently working as a Junior Front-End Developer in a software company.',
          color: '#f4c8d4',
          icon: 'mdi-laptop',
        },
      ],
    }),
}
</script>