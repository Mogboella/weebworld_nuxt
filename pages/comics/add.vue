<script>
export default {
    data() {
      return {
        name: '',
        author: '',
        type: '',
        genre: '',
        rating: '',
        write_status: ['Ongoing','Completed'],
        read_status: ['Not Started','Still Reading', 'Completed'],
        source: '',
        comments: '',
        }  
    },
    validations: {
        name: {
            required
        },
        type: {
            required
        },
        genre: {
            required
        },
        rating: {
            required
        },
        write_status: {
            required
        },
        read_status: {
            required
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
        }
    }
}
</script>
<template>
    
</template>