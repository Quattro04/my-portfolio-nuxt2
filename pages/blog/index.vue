<template>
    <div class="blog container h-screen flex flex-col bg-darkblue relative px-10 py-32 xl:p-40 mx-auto">
        <NuxtLink :to="'/blog/'+post.slug" class="item flex flex-col md:flex-row items-end bg-lightblue" v-for="post of posts" :key="post.slug">
            <div class="flex flex-1 flex-col w-full h-full justify-between p-5">
                <span class="text-green text-xl text-left">{{ post.title }}</span>
                <span class="text-offwhite text-left">{{ post.description }}</span>
                <span class="text-teal ml-auto">Read more</span>
            </div>
            <div class="flex flex-1 w-full h-full justify-center bg-black">
                <img :src="post.image">
            </div>
        </NuxtLink>
    </div>
</template>

<script>
export default {
    async asyncData({ $content }) {
        const posts = await $content("blog").fetch()
        return {
            posts
        }
    }
}
</script>

<style lang="scss">
    .blog {
        h1 {
            font-size: 100px;
        }
        .item {
            background-color: #2d3750;
            -webkit-box-shadow: 0px 5px 23px 1px #000000; 
            box-shadow: 0px 5px 23px 1px #000000;
        }
        .triangle {
            transition: all .3s;
            transform: rotate(85deg);
            &.top {
                width: 100%;
                height: 250%;
                top: -190%;
                left: 0%;
                background-color: #131a2c;
            }
        }
    }
</style>