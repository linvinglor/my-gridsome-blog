<template>
  <Layout>
      <!-- Page Header -->
  <header class="masthead"
  style="background-image: url('/img/about-bg.jpg')">
    <div class="overlay"></div>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div class="page-heading">
            <h1>{{about.title}}</h1>
            <span class="subheading">{{about.subtitle}}</span>
          </div>
        </div>
      </div>
    </div>
  </header>

  <!-- Main Content -->
  <div class="container">
    <div class="row">
      <div class="col-lg-8 col-md-10 mx-auto" v-html="about.content">
     </div>
    </div>
  </div>
  </Layout>
</template>
<page-query>
query{
  allStrapiAbout{
    edges{
      node{
        title
        subtitle
        content
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
    title: 'About us'
  },
   computed:{
    about(){
      return this.$page.allStrapiAbout.edges[0].node
    }
  }
}
</script>
