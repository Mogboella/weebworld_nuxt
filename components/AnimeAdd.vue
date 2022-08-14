<script>
export default {
    props: {
        close: Boolean
    },
    data() {
      return {
        name: '',
        genre: [],
        rating: '',
        anime_status: ['Ongoing','Completed'],
        watch_status: ['Not Started','Still Reading', 'Completed'],
        comments: '',
      }  
    },
    validations: {
        name: {required},
        rating: {required},
    },
    computed: {
        selectErrors () {
            const errors = []
            if (!this.$v.select.$dirty) return errors
            !this.$v.select.required && errors.push('Pick an option !!')
            return errors
        },
        nameErrors () {
            const errors = []
            if (!this.$v.name.$dirty) return errors
            !this.$v.name.required && errors.push('Name is required.')
            return errors
        },
        ratingErrors () {
            const errors = []
            if (!this.$v.rating.$dirty) return errors
            !this.$v.rating.required && errors.push('Rating is required.')
            return errors
        },
    },
    methods: {
        submit() {
            console.log('submit!')
            this.$v.$touch()
            if (this.$v.$invalid) {
                this.submitStatus = 'ERROR'
            } else {
                // do your submit logic here
                this.submitStatus = 'PENDING'
                setTimeout(() => {
                this.submitStatus = 'OK'
                }, 500)
            }
        },
        reset () {
            this.$refs.form.reset()
        },
        resetValidation () {
            this.$refs.form.resetValidation()
        },
        submitAnother(){
            this.submit()
            this.reset()
        },
        submitAndClose(){
            this.submit()
            this.close = true
        }
    },
    
}
</script>
<template>
    <v-card>
        <form>
            <v-btn @click="submitAndClose">Submit</v-btn>
            <v-btn @click="submitAnother">Add Another</v-btn>
        </form>
    </v-card>
</template>