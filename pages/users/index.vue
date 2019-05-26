<template>
    <section>
        <h1>Users page</h1>
        <ul>
           
            <li v-for="user in users" :key="user.id">
                 <a href="#" @click.prevent=goTo(user)>{{user.name}} ({{user.email}})</a>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    // nuxt js понимает какие поля мы возвращаем в async дата и они объеденятся с обычной data
    // Для того что бы сформировать дату на сервере
    // async asyncData({store, error}) {
    //     try {
    //         await store.dispatch('users/fetchUsers')
    //         return {}
    //     } catch (e) {
    //         error(e)
    //     }
    // },
    // отличие от asyncData не нужно ничего возвращать

    // async fetch({store, error}) {
    //     try {
    //         await store.dispatch('users/fetchUsers')
    //     } catch (e) {
    //         error(e)
    //     }
    // },

    data () {
        return {
            pageTitle: 'Users page'
        }
    },
    computed: {
        users () {
            return this.$store.getters['users/users']
        }
    },
    methods: {
        goTo(user) {
            this.$router.push('users/'+ user.id)
        }
    }
}
</script>
