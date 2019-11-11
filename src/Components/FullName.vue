<template>
    <div class="form-group">
        <label for="exampleInputEmail1">Full Name</label>
            <input 
                type="name" 
                class="form-control" 
                id="exampleInputFullName1" 
                aria-describedby="nameHelp" 
                placeholder="Enter Full Name"
                v-model.lazy="myName"
                v-on="listening(this.myName)">

    </div>
</template>

<script>
    export default {
        props: {
        },
        data() {
            return {
                myName: ''
            }
        },
        methods: {
            listening(input) {
                this.$emit('updateUser', input);
            }
        },
        computed: {
            
        }
    }
</script>

<style scoped>

</style>