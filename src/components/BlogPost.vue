<template>
  <article class="blog-post">
    <header class="post-header">
      <img :src="post.image" :alt="post.title" class="post-image">
      <div class="post-meta">
        <time :datetime="post.date">{{ formatDate(post.date) }}</time>
        <span class="reading-time">{{ post.readingTime }} min read</span>
      </div>
    </header>

    <div class="post-content">
      <h1 class="post-title">{{ post.title }}</h1>
      <p class="post-excerpt">{{ post.excerpt }}</p>
      <div class="post-body" v-html="post.content"></div>
    </div>

    <footer class="post-footer">
      <div class="author">
        <img :src="post.author.avatar" :alt="post.author.name" class="author-avatar">
        <div>
          <p class="author-name">{{ post.author.name }}</p>
          <p class="author-bio">{{ post.author.bio }}</p>
        </div>
      </div>
    </footer>
  </article>
</template>

<script>
export default {
  name: 'BlogPost',
  props: {
    post: {
      type: Object,
      required: true
    }
  },
  methods: {
    formatDate(date) {
      return new Date(date).toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      });
    }
  }
}
</script>

<style scoped>
.blog-post {
  max-width: 680px;
  margin: 0 auto;
  padding: 1rem;
}

.post-image {
  width: 100%;
  height: auto;
  border-radius: 8px;
  margin-bottom: 1rem;
}

.post-meta {
  display: flex;
  justify-content: space-between;
  color: #666;
  font-size: 0.875rem;
  margin-bottom: 1rem;
}

.post-title {
  font-size: 2rem;
  line-height: 1.2;
  margin-bottom: 1rem;
}

@media (min-width: 768px) {
  .blog-post {
    padding: 2rem;
  }

  .post-title {
    font-size: 2.5rem;
  }
}
</style>