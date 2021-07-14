<template>
    <div class="skills h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Social />
        <div class="container relative flex p-10 flex-col xl:p-0">
            <div class="flex">
                <div class="w-1/3 flex flex-col p-5">
                    <img src="/vue.png" width="80" height="80" />
                    <h2 class="text-offwhite text-2xl text-left mt-6 mb-4">Vue</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">I am a big fan of Vue.js. I love the fact that it's really easy to get into because it's just so intuitive, not to mention its great documentation. I've worked with it the longest and Nuxt is always my first choice when building a new web application.</p>
                </div>
                <div class="w-1/3 flex flex-col p-5">
                    <img src="/react.png" width="80" height="80" />
                    <h2 class="text-offwhite text-2xl text-left mt-6 mb-4">React</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">The thing that I like about React is that it's really unopinionated. It leaves most of the stuff to the developer. As a beginner this can be a bit overwhelming but as you become more experienced, you begin to enjoy the freedom this framework offers.</p>
                </div>
                <div class="w-1/3 flex flex-col p-5">
                    <img src="/angular.png" width="80" height="80" />
                    <h2 class="text-offwhite text-2xl text-left mt-6 mb-4">Angular</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">Recently I've been working a lot with Anuglar 10 due to work requirements and it's been very interesting. Though I am least experienced in this framework if comparing to other two, I'm beginning to like it more and more (typescript rules)</p>
                </div>
            </div>
            <div class="flex">
                <div class="w-1/3 flex flex-col p-5">
                    <img src="/css.png" width="80" height="80" />
                    <h2 class="text-offwhite text-2xl text-left mt-6 mb-4">CSS</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">I've worked with CSS constantly throughout my entire carrer. From plain CSS and enhanced syntax like scss, sass and less, to more recently css/ui frameworks like Tailwind, Vuetify, Element, Bulma, Quasar, Bootstrap and others. Also, playing around with CSS animations is one of my favorite things to do.</p>
                </div>
                <div class="w-1/3 flex flex-col p-5">
                    <img src="/node.png" width="80" height="80" />
                    <h2 class="text-offwhite text-2xl text-left mt-6 mb-4">Node</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">Node.js is of course my go-to backend choice as I've worked with it my entire career. The only thing that surprises me every time is the fact that it's so simple to set it up and run it but hey, who am I to complain.</p>
                </div>
                <div class="w-1/3 flex flex-col p-5">
                    <img src="/go.png" width="80" height="80" />
                    <h2 class="text-offwhite text-2xl text-left mt-6 mb-4">Go</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">I've been introduced to Go at work and have been playing around with it for a while now. I really love its superior performance characteristics compared to Node.js and the fact that you're not limited to a single thread simply by using goroutines.</p>
                </div>
            </div>
        </div>
        <img class="absolute bottom-0 left-0 hidden xl:block" src="/line-skills.png" data-not-lazy />
        <img class="line absolute hidden xl:block" src="/loop-green.png" data-not-lazy />
    </div>
</template>

<script>
export default {
    transition: {
        name: 'fade',
        mode: 'out-in'
    }
}
</script>

<style lang="scss">
    .skills {
        .symbol {
            font-family: 'Hack', sans-serif;
        }
        .line {
            right: 10%;
            transform: rotate(-45deg);
        }
    }

    .fade-enter-active, .fade-leave-active { transition: opacity .5s; }
    .fade-enter, .fade-leave-active { opacity: 0; }
</style>