<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <h3 class="mt-2">Moroccan university</h3>
        <v-autocomplete
          v-model="select"
          :loading="loading"
          :items="items"
          :search-input.sync="search"
          hide-no-data
          outlined
          item-text="Description"
          hide-selected
          clearable
          return-object
          label="Moroccan university"
          :required="required"
          :rules="[
            v =>
              !this.required ||
              !!v ||
              'Please choose one of the university above'
          ]"
        />
        <div style="padding: 10px ">
          <UniversityCard
            :name="searchedText[0].name"
            :link="searchedText[0].web_pages"
            :country="searchedText[0].country"
            v-if="searchedText !== null"
          />
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import UniversityCard from "@/components/UniversityCard";

export default {
  name: "Select",
  data: () => ({
    university: [{}],
    select: null,
    search: null,
    items: [],
    loading: false,
    searchedText: null,
    required: true
  }),
  components: {
    UniversityCard
  },
  created() {
    fetch("http://universities.hipolabs.com/search?country=Morocco")
      .then(res => res.json())
      .then(res => {
        this.university = res;
        this.items = res.map(u => u.name);
      });
  },
  watch: {
    search(query) {
      if (query && (!this.select || this.select.text !== query)) {
        this.searchedText = this.university.filter(f => f.name === query);
        console.log(this.searchedText[0].name);
      }
    }
  }
};
</script>
