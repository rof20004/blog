<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      app
      :width="350"
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title d-flex justify-center">
            <v-img
              lazy-src="https://picsum.photos/id/11/10/6"
              max-height="200"
              max-width="200"
              src="/itsme.jpg"
              class="rounded-circle"
            />
          </v-list-item-title>
          <v-list-item-subtitle class="text-center overline mt-4">
            <div class="white darken-2 text-center black--text text-wrap">
              Software Developer, Musician, Food lover and Father
            </div>
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider />

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          nuxt
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      fixed
    >
      <v-app-bar-nav-icon
        v-if="$vuetify.breakpoint.mobile"
        aria-label="Abrir drawer"
        @click.stop="drawer = !drawer"
      />

      <v-toolbar
        flat
        dense
      >
        <v-spacer v-if="$route.path !== '/'" />

        <v-btn
          v-if="$route.path !== '/'"
          depressed
          to="/"
        >
          <v-icon>
            mdi-arrow-left
          </v-icon>
          Voltar
        </v-btn>

        <v-text-field
          v-if="$route.path === '/'"
          hide-details
          prepend-icon="mdi-magnify"
          single-line
          label="Pesquisar artigo"
        />
      </v-toolbar>
    </v-app-bar>

    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      items: [
        {
          icon: 'mdi-apps',
          title: 'Artigos',
          to: '/'
        }
      ],
      drawer: !this.$vuetify.breakpoint.mobile
    }
  }
}
</script>
