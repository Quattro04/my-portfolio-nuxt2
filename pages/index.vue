<template>
    <div class="home h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Navigation />
        <Social />
        <div class="text flex flex-1 flex-col flex-wrap items-center absolute z-20 xl:items-start" @click="clicked">
            <transition name="fade">
                <div v-if="shown" class="matija flex h-48">
                    <span>MATIJA</span>
                    <div class="line active absolute hidden xl:block" />
                </div>
            </transition>
             <transition name="fade">
                <div v-if="shown" class="jeras flex h-48">
                    <span>JERAS</span>
                    <div class="line active absolute hidden xl:block" />
                </div>
            </transition>
            <transition name="fade">
                <h1 v-if="shown" class="text-2xl leading-8 py-8">Frontend developer with a passion for clean design</h1>
            </transition>

            <button class="touch touch--effect" :class="' ' + touchTrigger">
                <i class="touch__icon fa fa-fw fa-play"></i>
                <span class="touch__text">Play</span>
            </button>

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
    data() {
        return {
            touchTrigger: '',
            nameActive: '',
            interval: '',
            shown: false
        }
    },
    mounted() {
        this.shown = true;

        if (this.isMobile) {
            this.interval = setInterval(() => {
                this.touchTrigger = 'touch--click'
                setTimeout(() => {
                    this.touchTrigger = ''
                }, 500)
            }, 2000)
        } else {
            setTimeout(() => {
                var nextParticle = new NextParticle(document.all.logo)
            }, 300)
        }
    },
    methods: {
        clicked() {
            if (this.isMobile) {
                this.nameActive == '' ? this.nameActive = 'active' : this.nameActive = ''
            }
        }
    },
    computed: {
        isMobile() {
            return window.innerWidth < 1280
        }
    },
    transition: {
        name: 'fade',
        mode: 'out-in'
    }
}
</script>

<style lang="scss">
    .text {
        left: 10%;
        color: #eee;
        line-height: 1;
        span,
        a {
            display: flex;
            font-size: 200px;
            transition: all .3s;
            -webkit-touch-callout: none; /* iOS Safari */
            -webkit-user-select: none; /* Safari */
            user-select: none;
        }
        h1 {
            font-family: 'Poppins', sans-serif;
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
                font-size: 150px;
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
            left: -94%;
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

    .matija .line {
        transform: translateY(-105px);
    }
    .jeras .line {
        transform: translateY(85px);
    }

    .matija,
    .jeras {
        font-family: 'Devant Horgen', sans-serif;
        .line {
            width: 150px;
            height: 3px;
            left: -193px;
            top: 40%;
            background-color: #00ff95;
        }   
    }

    // ------------------ Touch indicator
    .touch {
        position: relative;
        display: inline-block;
        margin: 1em;
        padding: 0;
        border: none;
        background: none;
        color: #286aab;
        font-size: 1.4em;
        transition: color 0.7s;
    }

    .touch.touch--click,
    .touch:focus {
        outline: none;
        color: #3c8ddc;
    }

    .touch__icon {
        display: block;
    }

    .touch__text {
        position: absolute;
        opacity: 0;
        pointer-events: none;
    }

    .touch::after {
        content: '';
        position: absolute;
        top: 50%;
        left: 50%;
        margin: -35px 0 0 -35px;
        width: 70px;
        height: 70px;
        border-radius: 50%;
        opacity: 0;
        pointer-events: none;
    }

    .touch--effect::after {
        background: rgba(101, 158, 211, 0.1);
    }

    .touch--effect.touch--click::after {
        animation: anim-effect 0.5s forwards;
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
</style>
