<!-- u24673898 Franky -->
<template>
  <div v-if="post" class="blog-container">
    <div class="blog-header">
      <h1 class="blog-title">{{ post.Title }}</h1>
      <div class="blog-meta">
        <span class="meta-item"><strong>Author:</strong> {{ post.Author }}</span>
        <span class="meta-divider">•</span>
        <span class="meta-item"><strong>Category:</strong> {{ post.Category }}</span>
      </div>
    </div>
    
    <!-- Handle Content based on its structure -->
    <div class="blog-content">
      <div v-if="Array.isArray(post.Content)">
        <div v-for="(block, index) in post.Content" :key="index">
          <p v-if="block.type === 'paragraph'" class="content-paragraph">
            <span v-for="(child, childIndex) in block.children" :key="childIndex">
              {{ child.text }}
            </span>
          </p>
        </div>
      </div>
      <div v-else-if="typeof post.Content === 'string'" v-html="post.Content" class="content-html"></div>
    </div>
    
    <div v-if="post.snippet" class="blog-summary">
      <h3 class="summary-title">Summary</h3>
      <p class="summary-text">{{ post.snippet }}</p>
    </div>
  </div>
  
  <div v-else class="not-found-container">
    <h1>Post not found</h1>
    <p>The requested post could not be found.</p>
    <NuxtLink to="/" class="back-link">← Back to Home</NuxtLink>
  </div>
</template>

<script setup>
const route = useRoute()
const documentId = route.params.slug

// Fetch post by documentId using the correct URL
const { data: post } = await $fetch(`http://localhost:1337/api/blog-posts/${documentId}`)

// Set page meta
if (post) {
  useHead({
    title: post.Title || 'Blog Post'
  })
}
</script>

<style scoped>
@import '~/css/blog.css';
</style>