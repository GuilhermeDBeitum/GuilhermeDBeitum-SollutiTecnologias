<template>
  <v-app>
    <v-app-bar height="50" app color="orange" dark>
      <v-row class="text-center">
        <v-col md="12" cols="12">
          <router-link style="color:white; text-decoration:none;" to="/">
            <img height="58" src="~/assets/imgs/solluti-logo.jpg" />
          </router-link>
        </v-col>
      </v-row>
    </v-app-bar>
    <router-view></router-view>
    <v-footer app height="30" color="orange">
      <span style="color:white;">&copy; Solluti Tecnologias 2020. Todos os direitos reservados.</span>
    </v-footer>
  </v-app>
</template>



<script>
import Galeria from '~/components/Galeria.vue'

export default {
  components: { Galeria },

  data: () => ({
    //
  }),
}
</script>
