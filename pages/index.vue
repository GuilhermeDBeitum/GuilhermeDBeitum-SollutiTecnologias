<template>
  <router-link style="color: black; text-decoration: none;" to="Gallery">
    <v-app>
      <v-row align="center" justify="center">
        <img class="handfix" width="380" src="~assets/imgs/hand.png"
      /></v-row>
    </v-app>
  </router-link>
</template>
<style scoped>
.handfix {
  margin-left: 80px;
  bottom: 0;
  position: fixed;
}
</style>

<script>
export default {
  components: {},

  data: () => ({
    //
  }),
}
</script>
