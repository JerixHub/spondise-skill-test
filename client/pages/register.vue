<template>
  <div>
    <b-row>
        <b-col cols="6" class="mx-auto">
            <b-card>
                <b-form @submit.prevent="register">
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
                name: '',
                email: '',
                password: '',
            }
        }
    },

    methods: {
        async register(){
            try{
                await this.$axios.$get('http://spondise.test/sanctum/csrf-cookie');
                const response = await this.$axios.post('http://spondise.test/api/register', this.form);
                this.$auth.loginWith('laravelSanctum', {data: this.form})
            }catch(error){
                console.log(error);
            }
        }

        
    }
}
</script>
