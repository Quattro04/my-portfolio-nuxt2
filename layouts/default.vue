<template>
    <div class="main">
        <Navigation />
        <Nuxt />
    </div>
</template>

<style>

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
        font-family: 'Poppins', sans-serif;
    }
</style>
