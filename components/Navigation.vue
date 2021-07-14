<template>
    <nav :class="{background: background}" class="navigation w-5/6 justify-center flex text-md text-offwhite font-bold absolute top-0 z-20 p-10">
        <nuxt-link to="/" class="link px-10">Home</nuxt-link>
        <nuxt-link to="/skills" class="link px-10">Skills</nuxt-link>
        <nuxt-link to="/about" class="link px-10">About</nuxt-link>
        <nuxt-link to="/blog" class="link px-10">Blog</nuxt-link>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            background: false
        }
    },
    mounted() {
        this.checkBg()
    },
    methods: {
        checkBg() {
            if (window.location.href.includes('/blog/')) this.background = true
            else this.background = false
        }
    },
    watch:{
        $route (to, from){
            this.checkBg()
        }
    } 
}
</script>

<style lang="scss">
    .navigation {
        left: 50%;
        transform: translateX(-50%);
        .link {
            transition: color .3s;
            &:hover {
                color: #00ff95;
            }
        }

        .nuxt-link-exact-active {
            opacity: 0.5;
            pointer-events: none;
        }

        &.background {
            background-color: #0d1321;
        }
    }
</style>