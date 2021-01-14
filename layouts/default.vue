<template>
    <div class="main">
        <Nuxt />
    </div>
</template>

<style>

    @font-face {
    font-family: 'Devant Horgen';
    src: url('/fonts/devant/Devant Horgen.eot'); /* IE9 Compat Modes */
    src: url('/fonts/devant/Devant Horgen.woff') format('woff'), /* Modern Browsers */
        url('/fonts/devant/Devant Horgen.ttf')  format('truetype'), /* Safari, Android, iOS */
        url('/fonts/devant/Devant Horgen.svg#DevantHorgen-Medium') format('svg'); /* Legacy iOS */
    }

    @font-face {
    font-family: 'Hack';
    src: url('/fonts/hack/Hack-Regular.ttf')  format('truetype');
    }

    html {
        -ms-text-size-adjust: 100%;
        -webkit-text-size-adjust: 100%;
        -moz-osx-font-smoothing: grayscale;
        -webkit-font-smoothing: antialiased;
        box-sizing: border-box;
    }

    body {
        text-align: center;
    }

    *,
    *::before,
    *::after {
        box-sizing: border-box;
        margin: 0;
    }

    .main {
        background-color: #0d1321;
    }
</style>
