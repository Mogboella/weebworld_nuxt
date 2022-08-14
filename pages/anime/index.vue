<!-- TODO card view and list view. Button on top to select. -->
<!-- TODO card view and list view. Button on top to select. -->
<script>
import BookCard from "~/components/BookCard.vue";
import AnimeAdd from '../../components/AnimeAdd.vue';
export default {
  head() {
    return {
      title: "Anime"
    };
  },
  components: {
    BookCard,
    AnimeAdd
  },
  async asyncData({ $axios, params }) {
    try {
      let anime = await $axios.$get(`/anime/`);
      return { anime };
    } catch (e) {
      return { anime: [] };
    }
  },
  data() {
    return {
      anime: [],
      dialog: false
    };
  },
  methods: {
    async deleteAnime(recipe_id) {
      try {
        await this.$axios.$delete(`/anime/${recipe_id}/`); // delete recipe
        let newAnime = await this.$axios.$get("/anime/"); // get new list of Anime
        this.anime = newAnime; // update list of Anime
      } catch (e) {
        console.log(e);
      }
    }
  }
};
</script>
<template>
   <v-card>
    <v-card-title>Anime
        <v-spacer/>
        <v-dialog
            v-model="dialog"
            max-width="600px"
            >
            <template v-slot:activator="{ on, attrs }">
                <v-btn
                    color="primary"
                    dark
                    v-bind="attrs"
                    v-on="on"
                    >
                    Add Anime
                </v-btn>
            </template>
            <anime-add :close="dialog"/>
        </v-dialog>
    </v-card-title>
    
    <v-card-text>
        <v-row>
            <v-col v-for="show in anime" :key="show.id">
                <book-card :onDelete="deleteAnime" :book="show"></book-card>
            </v-col>
        </v-row>
    </v-card-text>
   </v-card>
</template>
