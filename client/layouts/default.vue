<template>
<div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand to="/">Home</b-navbar-brand>
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item to="/login">Login</b-nav-item>
        <b-nav-item to="/dashboard">Dashboard</b-nav-item>
        <b-nav-item href="#" @click.prevent="logout()">Sign Out</b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
  <Nuxt />
</div>


</template>

<script>
export default{
    methods: {
        async logout(){
            this.$auth.logout()
        }
    }
}
</script>