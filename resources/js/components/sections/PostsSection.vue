<template>
    <section class="posts">
        <div class="container">
            <ul class="row">
                <li class="col-4 mb-5" v-for="post in posts" :key="post.slug">
                    {{ post.title }}
                </li>
            </ul>
        </div>
    </section>
</template>

<script>
export default {
    name: "PostsSection",
    data() {
        return {
            posts: [],
        };
    },
    created() {
        axios
            .get("/api/posts")
            .then((response) => {
                this.posts = response.data;
            })
            .catch((e) => {
                console.log(e);
            });
    },
};
</script>

<style lang="scss" scoped></style>
