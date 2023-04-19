<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      src="https://cdn.create.vista.com/api/media/medium/229788058/stock-photo-smoky-grey-swirls-black-background?token="
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>{{ title }}</v-toolbar-title>
      <v-spacer />    
      <v-btn icon  @click="contact('https://www.linkedin.com/in/firdesbeyzanursenocak/')">
        <v-icon>mdi-linkedin</v-icon>
      </v-btn>

      <v-btn icon @click="contact('https://github.com/Firdesbeyzanur')">
        <v-icon>mdi-github</v-icon>
      </v-btn>
      <a href="mailto:beyzanursenocak96@gmail.com" style="text-decoration: none;">
      <v-btn icon>
        <v-icon>mdi-gmail</v-icon>
      </v-btn>
    </a>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <!-- <v-footer
      :absolute="!fixed"
      :right="right"
      style="background-image: url(https://t3.ftcdn.net/jpg/03/00/33/66/360_F_300336600_mK1HnvRXgDqBPSN90xEBQQjA8fFf9z6l.jpg); background-size: 100% 100%;"
    >
      <v-col
      class="text-center"
      cols="12"
    >
      <strong>{{ new Date().getFullYear() }}</strong>
    </v-col>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-view-dashboard',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-help-box',
          title: 'About Me',
          to: '/about'
        },
        {
          icon: 'mdi-image',
          title: 'Portfolio',
          to: '/portfolio'
        },
        {
          icon: 'mdi-file-document',
          title: 'Certificates',
          to: '/certificates'
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Firdes Beyzanur Senocak'
    }
  },
  methods: {
    contact: function (link) {
      window.open(link, '_blank');
    },
  }
}
</script>

