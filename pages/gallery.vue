<template>
  <v-app>
    <v-container fluid>
      <v-overlay :value="loading">
        <v-card-text>
          Carregando...
          <v-progress-linear
            indeterminate
            color="white"
            class="mb-0"
          ></v-progress-linear>
        </v-card-text>
      </v-overlay>
      <v-row>
        <v-col cols="3" md="3">
          <div class="box">
            <div
              style="color: black; text-decoration: none;"
              to="SubAnalises"
              class="media-post"
            >
              <v-img
                src="https://picsum.photos/511/120?random"
                aspect-ratio="2"
              >
                <div class="middle">
                  <span class="ctr">ANÁLISES</span>
                </div>
              </v-img>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<style scoped>
.ctr {
  margin: 50px;
  color: white;
  font-weight: 1120px;
  display: inline-block;
  border-radius: 11px;
  box-shadow: 0 35px 25px rgba(0, 0, 0, 0.2);
}

.media-post {
  margin-top: 35px;
  display: block;
  padding: 2px;
  border-radius: 8px;
  box-shadow: 0 25px 1px rgba(0, 0, 0, 0.2);
  background: black;
  text-align: center;
  text-align-last: center;
}

.middle {
  transition: 0.5s ease;
  opacity: 0;
  background-color: rgba(0, 8, 0, 0.7);
  font-size: 14px;
  text-align: center;
  text-align-last: center;
  height: 145px;
}

.dw {
  transition: 0.5s ease;
  position: absolute;
  top: 250%;
  left: 100%;
}

.box:hover .image {
  opacity: 0.3;
}

.box:hover .middle {
  opacity: 1;
}
</style>

<script>
export default {
  name: '',
  components: {},
  props: {
    source: String,
  },

  data: () => ({
    loading: false,
    photos: [],
    posts: [],
  }),

  computed: {
    headers() {
      return [
        { title: 'start', text: 'Titulo', value: 'title', width: 300 },
        { text: 'Corpo', value: 'body', width: 350 },
      ]
    },
  },

  methods: {
    listPosts() {
      let title = []
      let body = []

      console.log(this.posts)

      // this.posts.forEach((x) => {
      //   title.push(x.title)
      //   body.push(x.body)
      // })

      // return [
      //   {
      //     data: title,
      //   },
      //   {
      //     data: body,
      //   },
      // ]
    },

    async loadPosts() {
      this.loading = true
      try {
        let response = await this.$axios.get(
          'https://jsonplaceholder.typicode.com/posts',
          {
            headers: {
              'Content-Type': 'application/x-www-form-urlencoded;charset=UTF-8',
            },
          }
        )

        let data = response
        console.info(response)
        if (typeof data !== 'string') {
          this.posts = data

          this.listPosts()
        } else {
          this.$snotify.error(
            'Oops, ocorreu um erro ao carregar as informações da galeria!',
            'Atenção'
          )
        }
      } catch (error) {
        ''(error)
      } finally {
        this.loading = false
      }
    },

    async loadPhotos() {
      this.loading = true
      try {
        let response = await this.$axios.get(
          'https://jsonplaceholder.typicode.com/photos',
          {
            headers: {
              'Content-Type': 'application/x-www-form-urlencoded;charset=UTF-8',
            },
          }
        )

        let data = await response

        if (typeof data !== 'string') {
          this.photos = data
        } else {
          this.$snotify.error(
            'Oops, ocorreu um erro ao carregar imagens da galeria!',
            'Atenção'
          )
        }
      } catch (error) {
        ''(error)
      } finally {
        this.loading = false
      }
    },
  },

  mounted() {
    this.loadPhotos()
    this.loadPosts()
  },
}
</script>
