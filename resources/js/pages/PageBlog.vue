<template>
    <div>
        <h1 class="text-center">Boolpress</h1>
        <div class="row g-2">
            <CardPost v-for="post in posts" :key="post.id" :post="post" />
        </div>
        <nav aria-label="Page navigation example">
            <ul class="pagination justify-content-center">
                <li class="page-item">
                <a class="page-link" href="#" aria-label="Previous">
                    <span aria-hidden="true">&laquo;</span>
                </a>
                </li>
                <li class="page-item"><a class="page-link" href="#">1</a></li>
                <li class="page-item"><a class="page-link" href="#">2</a></li>
                <li class="page-item"><a class="page-link" href="#">3</a></li>
                <li class="page-item">
                <a class="page-link" href="#" aria-label="Next">
                    <span aria-hidden="true">&raquo;</span>
                </a>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script>
import CardPost from '../components/CardPost.vue';

export default {
    name: 'PageBlog',
    components: {
        CardPost,
    },
    data() {
        return {
            baseUrl: window.location.origin,
            posts: []
        }
    },
    created() {
        axios.get('/api/posts')
            .then(res => {
                this.posts = res.data.response.data;
                console.log(res);
            })
            .catch(error => console.log('errore!!!!!'));
    }
}
</script>

<style lang="scss" scoped>
    @import 'bootstrap/scss/bootstrap';
</style>
