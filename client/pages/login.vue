<template>
<div>
    <b-card>
        <b-form @submit="login()">
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

            <b-button type="submit" variant="primary">Submit</b-button>
        </b-form>
    </b-card>
  </div>


</template>

<script>
export default {
    auth: false,

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
            .then(response => console.log(response))
            .catch(error => console.log(error));
        }
    }

}
</script>
