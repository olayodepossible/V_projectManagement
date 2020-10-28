<template>
  <v-app background-color="grey-lighten-3 !important">
    <NavBar/>

    <v-main class="mx-4">
     <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
 import NavBar from "@/components/NavBar";
export default {
components:{
  NavBar
},

  data: () => ({
    //
  }),
};
</script>
