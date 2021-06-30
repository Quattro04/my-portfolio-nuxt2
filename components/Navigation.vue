<template>
    <nav class="navigation flex text-md text-white font-bold absolute top-0 z-20 p-10">
        <nuxt-link to="/" class="link px-10">Home</nuxt-link>
        <nuxt-link to="/skills" class="link px-10">Skills</nuxt-link>
        <nuxt-link to="/about" class="link px-10">About</nuxt-link>
    </nav>
</template>

<style lang="scss">
    .navigation {
        left: 50%;
        transform: translateX(-50%);
        font-family: 'Poppins', sans-serif;

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
    }
</style>