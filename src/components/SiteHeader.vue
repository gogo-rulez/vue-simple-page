<template>
    <header class="header">

        <div class="header__inner_wrap">
            <h1 class="header__title">VueSimplePage</h1>

            <a
                role="button"
                class="header__nav_toggle"
                :class="{'is-active': navVisible}"
                @click="navVisible = !navVisible"></a>

            <transition name="slide-fade">
                <navigation
                    v-if="navVisible"
                    :desk-navigation="desktopNavTriggered" />
            </transition>
        </div>

    </header>
</template>

<script>
import Navigation from '@/components/Navigation';

export default {
    name: 'SiteHeader',

    data () {
        return {
            navVisible: false,
            desktopNavTriggered: false
        };
    },

    components: {
        Navigation
    },

    created () {
        window.addEventListener('resize', this.setNavVisible);
    },
    destroyed () {
        window.removeEventListener('resize', this.setNavVisible);
    },

    mounted () {
        this.navVisible = window.innerWidth > 1024;
        this.desktopNavTriggered = window.innerWidth > 1024;
    },

    methods: {
        setNavVisible () {

            // if window width is >= 1024, make the nav always visible, and set up desktopNavTriggered
            // if window width goes bellow 1024, reset the navVisible flag, and after 0.5 seconds, reset desktopNavTriggered
            // desktopNavTriggered is used to setup a 'is-desktop' class on the .navigation element which will hide the nav on width < 1024
            // if we don't set it up like this, then while resizing from desk to mob, the nav will automatically be opened because of this.navVisible = true and then closed

            const windowWidth = window.innerWidth;

            if (windowWidth < 1024) {

                if (this.desktopNavTriggered) {
                    this.navVisible = false;
                    setTimeout(() => {
                        this.desktopNavTriggered = false;
                    }, 500);
                }

                return;
            }

            this.desktopNavTriggered = true;
            this.navVisible = true;

        }
    }
};
</script>

<style lang="scss" scoped>

</style>
