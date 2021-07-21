<template>
    <div class="social flex justify-center items-center text-grey fixed text-3xl top-0 right-0 px-6 py-4 m-8 z-20 xl:text-offwhite">
        <a class="icon px-4 py-2 mr-8" href="https://github.com/Quattro04" target="_blank"><font-awesome-icon :icon="['fab', 'github']"/></a>
        <a class="icon px-4 py-2 mr-8" href="https://www.linkedin.com/in/matija-jeras/" target="_blank"><font-awesome-icon :icon="['fab', 'linkedin-in']"/></a>
        <a class="icon px-4 py-2" href="https://www.facebook.com/matija.jeras01" target="_blank"><font-awesome-icon :icon="['fab', 'facebook-f']"/></a>
        <div class="absolute left-0 bottom-0 w-px h-12 bg-green hidden xl:block" />
        <div class="absolute left-0 bottom-0 w-12 h-px bg-green hidden xl:block" />
        <div class="absolute right-0 top-0 w-12 h-px bg-green hidden xl:block" />
        <div class="absolute right-0 top-0 w-px h-12 bg-green hidden xl:block" />
    </div>
</template>

<style lang="scss" scoped>
    .icon {
        transition: color .5s;
        &:hover {
            color: #00ff95;
        }
    }
    @media(max-width: 1279px) {
        .social {
            top: 85px;
            right: 0;
            margin: 0;
            padding: 0;
            flex-direction: column;
            .icon {
                padding: 10px 20px;
                margin: 0;
                font-size: 25px;
            }
        }
    }
</style>