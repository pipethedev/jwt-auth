<template>
    <ul>

        <li>
            {{ user }}
            <router-link :to="{name:'home'}">Home</router-link>
        </li>
        <template v-if="authenticated">
                <li>
                    <router-link :to="{name:'signin'}">Sign In</router-link>
                </li>
                <li>
                    {{user.name}}
                </li>
                <li>
                    <router-link :to="{name:'dashboard'}">Dashboard</router-link>
                </li>
                <li>
                    <a href="#"> Log Out</a>
                </li>
        </template>
        <template v-else>
            <router-link :to="{name: 'signin'}">SignIn</router-link>
        </template>
    </ul>
</template>
<script>
    import { mapGetters } from 'vuex'
    export default{
        computed : {
            ...mapGetters({
                authenticated: 'auth/authenticated',
                user: 'auth/user',
            })
        }
    }
</script>