<template>
    <div class="row center">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Full Name: {{ user.fullName }}</p>
                        <p>Email: {{ user.email }} </p>
                        <p>Store in Database?: {{ savePasswordProperty }}</p>
                    </div>
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
                    <form v-show="!submitted">
                        <!-- NAME -->
                        <app-full-name
                            v-on:updateUser="updateUserName"
                        ></app-full-name>
                        <!-- EMAIL -->
                        <div class="form-group">
                            <label for="exampleInputEmail1">Email address</label>
                                <input 
                                    type="email" class="form-control" 
                                    id="exampleInputEmail1" 
                                    aria-describedby="emailHelp" 
                                    placeholder="Enter email"
                                    v-model.lazy="user.email">
                                <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
                        </div>
                        <!-- PASSWORD -->
                        <div class="form-group">
                            <label for="exampleInputPassword1">Password</label>
                            <input 
                                type="password" 
                                class="form-control" 
                                id="exampleInputPassword1" 
                                placeholder="Password"
                                v-model="user.password">
                            <span v-show="user.password.length > 0" class="text-secondary">show: {{ user.password }}</span>
                        </div>
                        <!-- PW BOOL -->
                        <div class="form-group form-check">
                            <p>Do you want to save your password?</p>
                            <app-switch
                                v-model="dataSwitch"
                                :savePassword="savePassword"
                            ></app-switch>
                        </div>
                        <button 
                            type="submit" 
                            class="btn btn-primary"
                            @click.prevent="submitted = true"    
                        >Submit</button>
                    </form>
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
                </div>
            </div>
        </div>
</template>

<script>
    import Switch from './Switch.vue';
    import FullName from './FullName.vue';
    export default {
        components: {
            appSwitch: Switch,
            appFullName: FullName
        },
        data() {
            return {
                user: {
                    fullName: '',
                    email: '',
                    password: '',
                    savePW: true,
                },
                dataSwitch: true,
                submitted: false,
                savePasswordProperty: 'Yes',
                updateUser: '',
            }
        },
        methods: {
            savePassword(bool) {
                if (bool) {
                        this.savePasswordProperty = 'Yes';
                        this.user.savePW = true;
                    } else {
                        this.savePasswordProperty = 'No';
                        this.user.savePW = false;
                    }
            },
            updateUserName(inputValue) {
                console.log(inputValue, 'calling');
                this.user.fullName = inputValue;
            }
        }
    }
</script>

<style scoped>
    
</style>