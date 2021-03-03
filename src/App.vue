<template>
    <div id="app">

        <site-header />

    </div>
</template>

<script>
import SiteHeader from '@/components/SiteHeader';

export default {
    name: 'App',

    components: {
        SiteHeader
    }
};
</script>

<style lang="scss">
@import "@/assets/scss/styles.scss";
</style>
