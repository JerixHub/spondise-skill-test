<template>
<div>
    <b-row>
        <b-col cols="6" class="mx-auto">
            <b-card>
                <b-form @submit.prevent="login()">
                    <b-form-group id="input-group-2" label="Email Address:" label-for="input-2">
                        <b-form-input
                        id="input-2"
                        v-model="form.email"
                        placeholder="Enter email"
                        required
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-3" label="Password:" label-for="input-3">
                        <b-form-input
                        id="input-3"
                        v-model="form.password"
                        type="password"
                        placeholder="Enter password"
                        required
                        ></b-form-input>
                    </b-form-group>
                    <b-button @click="$auth.loginWith('google')">Sign In with Google</b-button>
                    <b-button type="submit" variant="primary">Submit</b-button>
                </b-form>
            </b-card>
        </b-col>
    </b-row>
</div>


</template>

<script>
export default {
    
    middleware: ['guest'],

    data(){
        return{ 
            form:{
                email: '',
                password: '',
            }
        }
    },

    methods: {
        login(){
            this.$auth.loginWith('laravelSanctum', {data: this.form})
            .then(response => {
                
            })
            .catch(error => console.log(error));
        },

        // async asyncData({$auth, query}){
        //     await $auth.loginWith('google', {params: query})
        //     return {}
        // }
    }

}
</script>
