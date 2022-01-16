<template>
    <div class="home h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Social />
        <div class="text flex flex-1 flex-col flex-wrap items-center absolute z-20 xl:items-start">
            <transition name="fade">
                <div v-if="shown" class="flex name">Matija</div>
            </transition>
             <transition name="fade">
                <div v-if="shown" class="flex surname">Jeras</div>
            </transition>
            <transition name="fade">
                <h1 v-if="shown" class="text-lg xl:text-2xl leading-8 py-8">Software developer with a passion for frontend</h1>
            </transition>
        </div>
        <transition name="fade">
            <div v-if="shown" class="particles hidden flex-1 absolute right-0 z-10 hidden xl:flex">
                <div class="particle-box">
                    <img id="logo" class="next-particle hidden"
                        data-init-position="none"
                        data-init-direction="none"
                        data-fade-position="none"
                        data-fade-direction="none"

                        data-particle-gap="3"

                        data-width="900"
                        data-height="700"

                        data-max-width="700"
                        data-max-height="500"                    

                        data-mouse-force="30"

                        data-gravity="0.03"

                        data-noise="30"
                        src="/logo_white_square.png"
                        data-not-lazy
                    />
                </div>
            </div>
        </transition>
        <div class="top triangle absolute" />
        <div class="left triangle absolute" />
    </div>
</template>

<script>
export default {
    head() {
        return {
            script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
        };
    },
    data() {
        return {
            interval: '',
            shown: false
        }
    },
    mounted() {
        this.shown = true;
        setTimeout(() => {
            var nextParticle = new NextParticle(document.all.logo)
        }, 300)
    },
    transition: {
        name: 'fade',
        mode: 'out-in'
    }
}
</script>

<style lang="scss">
.home {
    .text {
        left: 10%;
        color: #eee;
        line-height: 1;
        span,
        a {
            display: flex;
            transition: all .3s;
            -webkit-touch-callout: none; /* iOS Safari */
            -webkit-user-select: none; /* Safari */
            user-select: none;
        }
        @media(max-width: 1279px) {
            top: 100px;
            left: 0;
            right: 0;
            bottom: 0;
            justify-content: space-around;
            padding: 50px 0;
            h1 {
                width: 300px;
                margin-bottom: auto;
            }
            span {
                font-size: 120px;
            }
            .touch {
                margin-bottom: auto;
            }
        }
    }

    .triangle {
        transition: all .3s;
        transform: rotate(45deg);
        &.top {
            width: 60%;
            height: 150%;
            top: -100%;
            left: 14%;
            background-color: #3e5c76;
        }
        &.left {
            width: 200%;
            height: 150%;
            top: -100px;
            left: -100%;
            background-color: #1d2d44;
        }
        @media(max-width: 1279px) {
            &.top {
                z-index: 10;
                width: 700px;
                height: 1500px;
                top: 50%;
                left: 50%;
                transform: translate(-113%, -70%) rotate(45deg);
            }
            &.left {
                width: 700px;
                height: 1500px;
                top: 50%;
                left: 50%;
                transform: translate(-100%, -30%) rotate(-45deg);
            }
        }
    }

    .name,
    .surname {
        font-size: 6rem;
        @media(max-width: 1279px) {
            font-size: 3rem;
        }
    }

    @keyframes anim-effect {
        0% {
            transform: scale3d(0.3, 0.3, 1);
        }
        25%, 50% {
            opacity: 1;
        }
        100% {
            opacity: 0;
            transform: scale3d(1.2, 1.2, 1);
        }
    }

    .fade-enter-active, .fade-leave-active { transition: opacity .5s; }
    .fade-enter, .fade-leave-active { opacity: 0; }

    .slide-enter-active, .slide-leave-active { transition: transform .5s; }
    .slide-enter, .slide-leave-to { transform: translateX(-400px); }
}
</style>
