<script>
export default {
    props: ["book", "onDelete"]
};
</script>

<template>
    <v-card
        class="mx-auto"
        max-width="400"
    >
        <!-- TODO add to backend later -->
        <!-- <v-img
            class="white--text align-end"
            height="200px"
            src="book.picture"
            >
        </v-img> -->
        
        <v-card-title>{{ book.name }}</v-card-title>
        <v-card-actions>
            <v-btn
                color="orange"
                text
                to="`/book/${book.id}/`"
            >
                View
            </v-btn>

            <v-btn
                color="orange"
                text
                to="`/book/${book.id}/edit/`"
            >
                Edit
            </v-btn>
            <v-btn
                color="orange"
                text
                @click="onDelete(book.id)"
            >
                Delete
            </v-btn>
        </v-card-actions>
    </v-card>
</template>