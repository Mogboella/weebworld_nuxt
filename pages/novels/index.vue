<!-- TODO card view and list view. Button on top to select. -->

<script>
import BookCard from "~/components/BookCard.vue";
export default {
  head() {
    return {
      title: "Novels"
    };
  },
  components: {
    BookCard
  },
  async asyncData({ $axios, params }) {
    try {
      let novels = await $axios.$get(`/novels/`);
      return { novels };
    } catch (e) {
      return { novels: [] };
    }
  },
  data() {
    return {
      novels: []
    };
  },
  methods: {
    async deleteNovel(recipe_id) {
      try {
        await this.$axios.$delete(`/novels/${recipe_id}/`); // delete recipe
        let newnovels = await this.$axios.$get("/novels/"); // get new list of novels
        this.novels = newnovels; // update list of novels
      } catch (e) {
        console.log(e);
      }
    }
  }
};
</script>
<template>
   <v-card>
    <v-card-title>Novels
        <v-spacer/>
        <v-btn to="/novels/add"> Add Novel </v-btn>
    </v-card-title>
    
    <v-card-text>
        <v-row>
            <v-col v-for="novel in novels" :key="novel.id">
                <book-card :onDelete="deleteNovel" :book="novel"></book-card>
            </v-col>
        </v-row>
    </v-card-text>
   </v-card>
</template>
