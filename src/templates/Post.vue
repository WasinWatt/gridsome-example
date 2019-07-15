<template>
  <BlogLayout>
    <div class="markdown-body">
      <h1>{{ $page.post.title }}</h1>
      <img :src="$page.post.featuredImage" alt="blog">
      <ul v-for="tag in $page.post.tags">
        <li><g-link>{{ tag.title }}</g-link></li>
      </ul>
      <div v-html="$page.post.content" />
    </div>
  </BlogLayout>
</template>

<page-query>
query Post ($path: String!) {
  post: post (path: $path) {
    title
    content
    featuredImage
    tags {
      title
    }
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.post.title
    }
  }
}
</script>
