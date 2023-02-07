<template>
    <div>
        <h1>Frontoffice in Vue</h1>
        <div class="row">
        <div v-for="post in arrPosts" :key="post.id" class="col-12">
            <div class="card index mb-3 m-auto" style="width: 60%;">
                <div class="row g-0">
                  <div class="col-md-4 d-flex">
                    <img :src="'/storage/' + post.uploaded_img" class="img-fluid rounded-start" :alt="post.title">
                  </div>
                  <div class="col-md-8 d-flex align-items-center">
                    <div class="card-body">
                      <h5 class="card-title">{{post.title}}</h5>
                      <p class="type text-uppercase">{{post.excerpt}}</p>
                      <a :href="'/posts/' + post.slug" class="btn btn-primary">Leggi</a>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
        </div>
    </div>

</template>

<script>

export default {
    name: 'App',
    data() {
        return {
            arrPosts: [],
        }
    },
    created() {
        axios.get('/api/posts')
            .then(response => this.arrPosts = response.data.results)

    },

}

</script>


<style lang="scss">
@import '~bootstrap/scss/bootstrap';

</style>
