<template>
    <nav
        v-if="navDataReady"
        class="navigation"
        :class="{'is-desktop': deskNavigation}">

        <ul class="navigation__list">

            <li
                v-for="route in routes"
                :key="route.name"
                class="navigation__list_item">

                <router-link
                    :to="{ name: route.name }"
                    class="navigation__link">
                    {{ route.name }}
                </router-link>

            </li>

        </ul>

    </nav>
</template>

<script>
export default {
    name: 'Navigation',

    props: {
        deskNavigation: Boolean
    },

    data () {
        return {
            routes: [],
            navDataReady: false
        };
    },

    mounted () {
        this.routes = this.$router.options.routes;
        this.navDataReady = true;
    }
};
</script>

<style lang="scss" scoped>
</style>
