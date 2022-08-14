<script>
export default {
    data: () => ({
      icons: ['mdi-rewind', 'mdi-play', 'mdi-fast-forward'],
      items: [
        {
          title: 'Novels',
          text: `Webnovel Favourites`,
          subtext: 'New novels. Updated daily.',
          color: '',
          src: '/novels',
        },
        {
          title: 'Manga',
          text: 'Your Manga, Manhwa and Manhua favourites',
          subtext: 'Lose yourself in 2d.',
          color: '',
          src: '/comics'
        },
        {
          title: 'Anime',
          text: 'Anime Hits',
          subtext: 'Cool Animes to binge on.',
          color: '',
          src: '/anime'
        },
      ],
      transparent: 'rgba(255, 255, 255, 0)',
    }),
  }
</script>
<template>
  <v-container class="pa-4 text-center">
        <v-row
        class="fill-height"
        align="center"
        justify="center"
        >
            <template v-for="(item, i) in items">
                <v-col
                    :key="i"
                    cols="12"
                    md="4"
                >
                    <v-hover v-slot="{ hover }">
                        <v-card
                        :elevation="hover ? 12 : 2"
                        :class="{ 'on-hover': hover }"
                        :to="item.src"
                        >
                            
                            <v-card-title class="text-h6 white--text">
                                <v-row
                                    class="fill-height flex-column"
                                    justify="space-between"
                                >
                                    <p class="mt-4 subheading text-left">
                                        {{ item.title }}
                                    </p>

                                    <div>
                                    <p class="ma-0 text-body-1 font-weight-bold font-italic text-left">
                                        {{ item.text }}
                                    </p>
                                    <p class="text-caption font-weight-medium font-italic text-left">
                                        {{ item.subtext }}
                                    </p>
                                    </div>
                                    <!-- <div class="align-self-center">
                                        <v-btn
                                            :class="{ 'show-btns': hover }"
                                            :color="transparent"
                                            :to="item.src"
                                            icon
                                        >
                                            <v-icon
                                                :class="{ 'show-btns': hover }"
                                                :color="transparent"
                                                >
                                                mdi-arrow-right-bold-circle-outline
                                            </v-icon>
                                        </v-btn>
                                    </div> -->
                                </v-row>
                            </v-card-title>
                        </v-card>
                    </v-hover>
                </v-col>
            </template>
        </v-row>
  </v-container>
</template>
<style scoped>
.v-card {
  transition: opacity .4s ease-in-out;
}

.v-card:not(.on-hover) {
  opacity: 0.6;
 }

.show-btns {
  color: rgba(255, 255, 255, 1) !important;
}
</style>