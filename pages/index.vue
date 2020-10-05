<template>
  <v-row
    justify="center"
    align="center"
  >
    <v-col cols="12">
      <template v-for="post in posts">
        <v-card
          :key="post.uuid"
          class="mb-8"
        >
          <v-card-title class="headline">
            {{ post.title }}
          </v-card-title>

          <v-card-text>
            <span>{{ post.date | date }}</span>
          </v-card-text>

          <v-card-text>
            <span class="text-h6">{{ post.description }}</span>
          </v-card-text>

          <v-card-actions>
            <v-btn
              color="primary"
              nuxt
              :to="post.path"
            >
              Ler artigo
            </v-btn>
          </v-card-actions>
        </v-card>
      </template>
    </v-col>
  </v-row>
</template>

<script>
export default {
  filters: {
    date (value) {
      return new Date(value).toLocaleString()
    }
  },

  data () {
    return {
      posts: []
    }
  },

  async mounted () {
    this.posts = await fetch('/posts.json').then(response => response.json())
  },

  head: {
    title: 'Home'
  }
}
</script>
