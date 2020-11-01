<template>
    <div class="home h-screen flex justify-center items-center text-center overflow-hidden bg-darkblue relative">
        <Social />
        <div class="text flex flex-1 flex-col flex-wrap items-center absolute z-20 xl:items-start" @click="clicked">
            <div class="matija flex h-48 overflow-hidden cursor-pointer" :class="' ' + nameActive">
                <span>MATIJ</span>
                <nuxt-link to="/about">
                    <span>A</span>
                    <span>BOUT</span>
                </nuxt-link>
                <div class="line absolute hidden xl:block" />
                <div class="line active absolute hidden xl:block" />
            </div>
            <div class="jeras flex h-48 overflow-hidden cursor-pointer" :class="' ' + nameActive">
                <span>JERA</span>
                <nuxt-link to="/skills">
                    <span>S</span>
                    <span>KILLS</span>
                </nuxt-link>
                <div class="line absolute hidden xl:block" />
                <div class="line active absolute hidden xl:block" />
            </div>
            <h1 class="text-2xl leading-8 py-8">Frontend developer with a passion for clean design</h1>

            <button class="touch touch--effect" :class="' ' + touchTrigger">
                <i class="touch__icon fa fa-fw fa-play"></i>
                <span class="touch__text">Play</span>
            </button>

        </div>
        <div class="particles hidden flex-1 absolute right-0 z-10 hidden xl:flex">
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
                />
            </div>
        </div>
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
            interval: ''
        }
    },
    mounted() {
        // Desktop
        var nextParticle = new NextParticle(document.all.logo)

        if (this.isMobile) {
            this.interval = setInterval(() => {
                this.touchTrigger = 'touch--click'
                setTimeout(() => {
                    this.touchTrigger = ''
                }, 500)
            }, 2000)
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
        name: 'home',
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
            .matija {
                width: 212px;
                height: 125px;
                margin-top: auto;
            }
            .jeras {
                width: 172px;
                height: 125px;
                margin-bottom: auto;
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
            left: 12%;
            background-color: #3e5c76;
        }
        &.left {
            width: 200%;
            height: 150%;
            top: -100px;
            left: -1900px;
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

    .matija {
        width: 289px;
        text-shadow: 5px 5px #0d1321;
        .line {
            transform: translateY(-90px);
            &.active {
                transform: translate(-100%, -90px);
            }
        }
        &:hover {
            > span,
            a {
                transform: translateX(-233px);
                
            }
            .line.active {
                transform: translate(0, -90px);
            }
        }
        &.active {
            > span,
            a {
                transform: translateX(-178px);
                color: #00ff95;
                &:first-child {
                    color: #eee;
                    margin-right: 20px;
                }
            }
        }
    }
    .jeras {
        width: 232px;
        text-shadow: 5px 5px #0d1321;
        transition: width .3s;
        .line {
            transform: translateY(+100px);
            &.active {
                transform: translate(-100%, +100px);
            }
        }
        &:hover {
            width: 280px;
            > span,
            a {
                transform: translateX(-179px);
            }
            .line.active {
                transform: translate(0, +100px);
            }
        }
        &.active {
            width: 200px;
            > span,
            a {
                transform: translateX(-152px);
                color: #00ff95;
                &:first-child {
                    color: #eee;
                    margin-right: 20px;
                }
            }
        }
    }

    .matija,
    .jeras {
        font-family: 'Devant Horgen', sans-serif;
        .line {
            width: 150px;
            height: 3px;
            background-color: #0d1321;
            left: -193px;
            top: 40%;
            transition: transform .3s;
            &.active {
                background-color: #00ff95;
            }
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

    .home-enter-active, .home-leave-active { transition: opacity .5s; }
    .home-enter, .home-leave-active { opacity: 0; }
</style>
