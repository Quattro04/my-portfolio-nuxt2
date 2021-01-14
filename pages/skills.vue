<template>
    <div class="skills h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Social />
        <div class="container relative flex p-10 flex-col xl:p-0">
            <h1 class="text-white text-3xl text-left mb-20">What I've worked with</h1>
            <div class="flex">
                <div class="w-1/3 flex flex-col mr-20">
                    <img src="/js.png" width="80" height="80" />
                    <h2 class="text-white text-2xl text-left mt-6 mb-4">Javascript</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">One may say that the Javascript world is where I spend most of my time when writing code. I really love Vue.js, I've worked with it the longest and it's still my primary frontend framework choice. Of course I know my way around React or lately Angular 10 too, also a bit of Svelte.js. On the backend, I worked a lot with Node.js.</p>
                </div>
                <div class="w-1/3 flex flex-col mr-20">
                    <img src="/css.png" width="80" height="80" />
                    <h2 class="text-white text-2xl text-left mt-6 mb-4">CSS</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">I've worked with CSS constantly throughout my entire carrer. From plain CSS and enhanced syntax like scss, sass and less, to more recently css/ui frameworks like Tailwind, Vuetify, Element, Bulma, Quasar, Bootstrap and others. Also, playing around with CSS animations is one of my favorite things to do.</p>
                </div>
                <div class="w-1/3 flex flex-col">
                    <!-- <span class="symbol text-green text-2xl text-left">if err != nil { }</span> -->
                    <img src="/go.png" width="80" height="80" />
                    <h2 class="text-white text-2xl text-left mt-6 mb-4">Go</h2>
                    <p class="text-fadedwhite text-md font-light text-left leading-7">I've been playing around with Go for a while now. I really love its superior performance characteristics compared to Node.js and the fact that you're not limited to a single thread simply by using goroutines. When choosing a language for backend, I'm beginning to lean more towards Go.</p>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .skills {
        font-family: 'Poppins', sans-serif;
        .symbol {
            font-family: 'Hack', sans-serif;
        }
    }
</style>