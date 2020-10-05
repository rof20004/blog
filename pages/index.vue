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
      posts: [
        {
          uuid: '8d262e87-836c-415c-afe5-9e13381223df',
          title: 'Como subir para produção um site estático com Nuxt e Netlify',
          date: '2020-10-04T22:34:14.839Z',
          description: 'Neste artigo vou mostrar como realizar o deploy de um site estático feito em Nuxt no Netlify, um dos mais rápidos CDN da atualidade, utilizando continuous delivery com github.',
          path: '/articles/8d262e87-836c-415c-afe5-9e13381223df'
        }
      ]
    }
  },

  head: {
    title: 'Home'
  }
}
</script>
