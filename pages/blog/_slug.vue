<template>
    <div class="blog-post h-screen flex flex-col bg-darkblue overflow-auto">
        <div class="container p-40 mx-auto text-fadedwhite text-left">
            <h1 class="text-left text-green text-3xl mb-2">{{ post.title }}</h1>
            <h2 class="text-left text-white mb-10">{{ post.description }}</h2>
            <nuxt-content :document="post" />
        </div>
    </div>
</template>

<script>
export default {
    async asyncData({ $content, params, error }) {
        let post;
        try {
            post = await $content("blog", params.slug).fetch();
            // OR const article = await $content(`articles/${params.slug}`).fetch()
        } catch (e) {
            error({ message: "Blog Post not found" });
        }

        return {
            post,
        };
    },
};
</script>

<style lang="scss">
    .blog-post {
        h3 {
            color: #5faac7;
            font-size: 24px;
            margin: 30px 0 10px;
        }
        h4 {
            color: white;
            font-size: 20px;
            margin: 20px 0 10px;
        }
        p {
            font-size: 16px;
            margin: 20px 0 10px;
        }
        .nuxt-content-highlight {
            margin: 20px 0;
            .line-numbers {
                background-color: #070a13;
                text-shadow: none;
                color: #4db8c3;
                ::selection {
                    background-color: #ffffff1c;
                }
            }
            .token.operator {
                background: none;
            }
        }
        p code {
            background-color: black;
            color: white;
        }
        ul li {
            padding-left: 20px;
            position: relative;
            &:before {
                content: "";
                position: absolute;
                left: 0;
                top: 7px;
                width: 8px;
                height: 8px;
                background-color: #5faac7;
                border-radius: 50%;
            }
        }
    }
</style>