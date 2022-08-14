<!-- TODO card view and list view. Button on top to select. -->
<!-- TODO card view and list view. Button on top to select. -->
<script>
import BookCard from "~/components/BookCard.vue";
export default {
  head() {
    return {
      title: "Comics"
    };
  },
  components: {
    BookCard
  },
  async asyncData({ $axios, params }) {
    try {
      let comics = await $axios.$get(`/comics/`);
      return { comics };
    } catch (e) {
      return { comics: [] };
    }
  },
  data() {
    return {
      comics: []
    };
  },
  methods: {
    async deletecomic(recipe_id) {
      try {
        await this.$axios.$delete(`/comics/${recipe_id}/`); // delete recipe
        let newcomics = await this.$axios.$get("/comics/"); // get new list of comics
        this.comics = newcomics; // update list of comics
      } catch (e) {
        console.log(e);
      }
    }
  }
};
</script>
<template>
   <v-card>
    <v-card-title>Comics
        <v-spacer/>
        <v-btn to="/comics/add"> Add Comic </v-btn>
    </v-card-title>
    
    <v-card-text>
        <v-row>
            <v-col v-for="comic in comics" :key="comic.id">
                <book-card :onDelete="deletecomic" :book="comic"></book-card>
            </v-col>
        </v-row>
    </v-card-text>
   </v-card>
</template>
