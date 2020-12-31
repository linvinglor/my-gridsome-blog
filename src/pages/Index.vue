<template>
  <Layout>
    <!-- Page Header -->
    <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="site-heading">
              <h1>{{general.title}} Blog</h1>
              <span class="subheading">{{general.subtitle}}</span>
            </div>
          </div>
        </div>
      </div>
    </header>
    <!-- Main Content -->
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div
            class="post-preview"
            v-for="edge in $page.posts.edges"
            :key="edge.node.id"
          >
            <g-link :to="'/post/' + edge.node.id">
              <h2 class="post-title">
                {{ edge.node.title }}
              </h2>
            </g-link>
            <p class="post-meta">Posted by on {{ edge.node.created_at }}</p>
            <hr />
          </div>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
query($page:Int){
  posts:allStrapiPost(perPage:10,page:$page) @paginate{
    edges{
      node{
        id
        title
        content
        created_at
      }
    }
  }
  allStrapiGeneral{
  edges{
    node{
      id
      title
      subtitle
      cover{
        url
      }
    }
  }
}
}

</page-query>
<script>
export default {
  metaInfo: {
    title: "homeName",
  },
  computed:{
    general(){
      return this.$page.allStrapiGeneral.edges[0].node
    }
  }
};
</script>

<style></style>
