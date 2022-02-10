<template>
  <v-app>
    <v-main>
      <v-container fluid>
        <v-row>
          <v-col cols="12">
            <HeaderBar />
          </v-col>
          <router-view />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import HeaderBar from "@/components/templates/HeaderBar.vue";
export default Vue.extend({
  name: "App",
  components:{
    HeaderBar
  },
  data: () => ({
    //
  }),
});
</script>
<style>

</style>