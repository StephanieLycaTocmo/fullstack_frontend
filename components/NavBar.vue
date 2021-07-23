<template>
    <div class="container">
        <div class="nav-bar">
            <b-navbar toggleable="sm" type="dark" variant="dark">
            <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>

            <b-navbar-brand href="/">
                <b>Authentication</b>
            </b-navbar-brand>

            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav class="ml-auto">
                    <template v-if="$auth.loggedIn">
                        <b-nav-item href="/dashboard"><b>Dashboard</b></b-nav-item>
                        <b-nav-item href="/items"><b>Items</b></b-nav-item>
                        <b-nav-item href="#" @click.prevent="onLogout"><b>Logout</b></b-nav-item>
                    </template>

                    <template v-else>
                        <b-nav-item href="/register"><b>Register</b></b-nav-item>
                        <b-nav-item href="/login"><b>Login</b></b-nav-item>
                    </template>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        async onLogout() {
            this.$auth.logout()
        }
    }
}
</script>

<style>
    b{
        text-align: center;
        font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }  
    .container{
        padding-top: 15px;
    } 
</style>