<template>
  <v-card class="mx-auto" max-width="400" height="250">
    <v-card-text>
      <div>Country : {{ this.$props.country }}</div>
      <h3 class="font-weight-black my-2 text--primary text-center">
        {{ this.$props.name }}
      </h3>
    </v-card-text>
    <v-card-text class="pb-0">
      <a
        :href="this.$props.link"
        target="_blank"
        class="v-btn v-btn--block v-btn--outlined py-5 px-5 text--primary"
      >
        Click here to visit university website
      </a>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: ["country", "link", "name"],
  name: "UniversityCard"
};
</script>

<style scoped></style>
