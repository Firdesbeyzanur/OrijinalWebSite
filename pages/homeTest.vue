<template>
    <v-carousel>
      <v-carousel-item>
        {{ items.src }}
      </v-carousel-item>
    </v-carousel>
  </template>

<script>
export default {
  data () {
    return {
      items: [
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg',
        }
      ],
    }
  },
}
</script>

<style scoped>
.pictures {
    height: 100px;
}
</style>