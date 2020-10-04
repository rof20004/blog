<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      app
      :width="350"
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title text-center">
            <v-img
              lazy-src="https://picsum.photos/id/11/10/6"
              :aspect-ratio="4/4"
              src="/itsme.jpg"
              class="rounded"
            />
          </v-list-item-title>
          <v-list-item-subtitle class="text-center overline mt-4">
            <div class="white darken-2 text-center black--text text-wrap">
              Software Developer, Gamer, Musician, Food lover and Father
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
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      fixed
    >
      <v-app-bar-nav-icon
        v-if="$vuetify.breakpoint.mobile"
        @click.stop="drawer = !drawer"
      />

      <v-toolbar
        flat
        dense
      >
        <v-text-field
          hide-details
          prepend-icon="mdi-magnify"
          single-line
          placeholder="Pesquisar artigo"
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
