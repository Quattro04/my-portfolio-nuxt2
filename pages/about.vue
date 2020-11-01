<template>
    <div class="about h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Social />
        <div class="container relative flex justify-between">
            <div class="flex flex-col justify-center items-start text-white mr-20">
                <div class="flex justify-start">
                    <h1>hey</h1>
                    <h2 class="ml-8 text-green">there.</h2>
                </div>
                <p class="text-left mt-5">I am Matija Jeras, a web developer focused on frontend code that enables me to program a clean and intuitive web based applications.</p>
                <p class="text-left mt-8">I'm always looking for new challenges and don't like to stagnate by doing easy repetitive work. That way my variety of skills is continuosly expanding, which I think is mandatory in today's fast changing technology.</p>
                <div class="flex mt-8">
                    <nuxt-link to="/" class="link px-6 py-4 mr-8">Home</nuxt-link>
                    <nuxt-link to="/skills" class="link px-6 py-4">Skills</nuxt-link>
                </div>
            </div>
            <img class="me" src="/me+.png" />
            <img class="absolute right-0 bottom-0" src="/image-line.png" />
        </div>
        <img class="loop absolute" src="/loop.png" />
    </div>
</template>

<style lang="scss">
    .about {
        font-family: 'Poppins', sans-serif;
        .loop {
            left: -100px;
            top: 80px;
        }
        p,
        h1 {
            font-size: 20px;
        }
        h1,
        h2 {
            font-size: 100px;
        }
        img.me {
            margin-right: -6.45rem;
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
                transition: height .5s;
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

