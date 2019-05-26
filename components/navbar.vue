<template>
    <header>
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">NuxtJs</a>
            <div class="collapse navbar-collapse">
                <ul class="navbar-nav mr-auto">
                <li class="nav-item">
                    <nuxt-link exact class="nav-link" active-class="active" to="/">Home </nuxt-link>
                </li>
                <li class="nav-item">
                    <!-- no-prefetch не подгружать множество страниц при загрузке одной страницы -->
                    <nuxt-link no-prefetch class="nav-link" active-class="active" to="/users">Users</nuxt-link>
                </li>
                 <li class="nav-item">
                    <nuxt-link no-prefetch class="nav-link" active-class="active" to="/about">About</nuxt-link>
                </li>
                  <li class="nav-item">
                    <nuxt-link no-prefetch class="nav-link" active-class="active" to="/login">Login</nuxt-link>
                </li>
                <li class="nav-item" v-if="isAuth">
                    <a class="nav-link" href="#" @click.prevent="logout()">Logout</a>
                </li>
                </ul>
            </div>
        </nav>
    </header>
</template>

<script>
export default {
    computed: {
        isAuth() {
            return this.$store.getters.isAuth
        }
    },
    methods: {
        logout() {
            this.$store.dispatch('logout')
        }
    }
}
</script>
