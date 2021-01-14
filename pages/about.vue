<template>
    <div class="about h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Social />
        <div class="container relative flex justify-between flex-col-reverse p-10 xl:flex-row xl:items-center xl:p-0">
            <div class="flex flex-col justify-center items-start text-white xl:mr-20">
                <div class="flex justify-start">
                    <h1>hey</h1>
                    <h2 class="ml-3 text-green xl:ml-8">there.</h2>
                </div>
                <p class="text-left mt-5">I am Matija Jeras, a web developer focused on frontend code that enables me to program a clean and intuitive web based applications.</p>
                <p class="text-left mt-8">I'm always looking for new challenges and don't like to stagnate by doing easy repetitive work. That way my variety of skills is continuosly expanding, which I think is mandatory in today's fast changing technology.</p>
                <div class="flex mt-8">
                    <nuxt-link to="/" class="link px-6 py-4 mr-8">Home</nuxt-link>
                    <nuxt-link to="/skills" class="link px-6 py-4">Skills</nuxt-link>
                </div>
            </div>
            <img class="me" src="/me+.png" />
            <img class="absolute right-0 bottom-0 hidden xl:block" src="/image-line.png" />
        </div>
        <img class="loop absolute hidden xl:block" src="/loop.png" data-not-lazy />
    </div>
</template>

<style lang="scss">
    .about {
        font-family: 'Poppins', sans-serif;
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
            margin-right: -6.45rem;
            @media(max-width: 1279px) {
                margin-right: 0;
                width: 300px;
            }
        }
        .link {
            border-bottom: 1px solid #00ff95;
            transition: all .3s;
            position: relative;
            &:hover {
                // background-color: #00ff95;
                // color: #0d1321;
                &:before,
                &:after {
                    height: 30%;
                }
            }
            &:before,
            &:after {
                content: '';
                width: 1px;
                height: 0;
                background-color: #00ff95;
                position: absolute;
                bottom: 0;
                transition: height .3s;
            }
            &:before {
                left: 0;
            }
            &:after {
                right: 0;
            }
        }
    }

</style>

