<template>
  <div>
    <b-card>
        <b-form @submit.prevent="register">
            <input type="hidden" id="csrf_token" name="csrf_token" value=""></input>
            <b-form-group
                id="input-group-1"
                label="Name:"
                label-for="input-1"
            >
                <b-form-input
                id="input-1"
                v-model="form.name"
                type="text"
                placeholder="Enter Name"
                required
                ></b-form-input>
            </b-form-group>

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
                name: '',
                email: '',
                password: '',
            }
        }
    },

    mounted(){
        this.$axios.$get('http://localhost:8000/sanctum/csrf-cookie');
    },

    methods: {
        register(){
            var formData = this.form;
            this.$axios.post('http://localhost:8000/api/register', formData)
            .then((response) => {
                console.log(response);
            }, (error) => {
                console.log(error);
            });
        }

        
    }
}
</script>
