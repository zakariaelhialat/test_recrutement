<template>
  <v-app>
    <v-app-bar app color="green" elevate-on-scroll dark>
      <h2 class="font-weight-black align-center">Vue university</h2>
    </v-app-bar>
    <v-main>
      <Select/>

    </v-main>
  </v-app>
</template>

<script>
import Select from "./components/Select";

export default {
  name: "App",
  components: {
    Select
  },

  data: () => ({
    //
  })
};
</script>
