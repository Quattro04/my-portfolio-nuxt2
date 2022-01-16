<template>
    <div class="about h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Social />
        <div class="container relative flex justify-between flex-col-reverse p-10 xl:flex-row xl:items-center xl:p-0">
            <div class="flex flex-col justify-center items-start text-offwhite xl:mr-20">
                <div class="flex justify-start">
                    <h1>hey</h1>
                    <h2 class="ml-3 text-green xl:ml-8">there.</h2>
                </div>
                <p class="text-left mt-5">I am Matija Jeras, a software developer focused on frontend code that enables me to program a clean and intuitive web based applications.</p>
                <p class="text-left mt-8">I'm always looking for new challenges and don't like to stagnate by doing easy repetitive work. That way my variety of skills is continuosly expanding, which I think is mandatory in today's fast changing technology.</p>
            </div>
            <div class="me-wrapper">
                <img class="me" src="/me.png" />
            </div>
            <img class="absolute right-0 bottom-0 hidden xl:block" src="/image-line.png" />
        </div>
        <img class="loop absolute hidden xl:block" src="/loop.png" data-not-lazy />
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
    .about {
        .loop {
            left: -100px;
            top: 80px;
        }
        p {
            font-size: 20px;
            @media(max-width: 1279px) {
                font-size: 16px;
            }
        }
        h1,
        h2 {
            font-size: 100px;
            @media(max-width: 1279px) {
                font-size: 50px;
            }
        }
        img.me {
            width: 100%;
            height: 100%;
            @media(max-width: 1279px) {
                width: 300px;
                height: auto;
            }
        }
        .me-wrapper {
            flex: 0 0 600px;
            height: 492px;
            margin-right: -6.45rem;
            @media(max-width: 1279px) {
                margin-right: 0;
                flex: 1 1 300px;
            }
        }
    }

    .fade-enter-active, .fade-leave-active { transition: opacity .5s; }
    .fade-enter, .fade-leave-active { opacity: 0; }
</style>

