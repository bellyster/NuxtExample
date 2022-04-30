<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
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
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
        <!-- Agregar un enlace con v-list-item -->
        <!-- <v-list-item to="/about-us">
          ABOUT US
        </v-list-item>
        <nuxt-link to="/about-us">About con nuxt</nuxt-link>
        <v-btn depressed to="/about-us">
          boton about
        </v-btn> -->
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      class="white--text"
      :clipped-left="clipped"
      fixed
      color="primary"
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="white--text"/>
      
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        },
        {
          icon: 'mdi-sprout ',
          title: 'Plantas',
          to: '/plantas'
        },
        {
          icon: 'mdi-account-box-outline',
          title: 'Contact',
          to: '/contact'
        },

      ],
      miniVariant: false,
      right: true,
      title: 'Vuetify.js'
    }
  }
}
</script>
