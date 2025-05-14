<!-- u24673898 Franky -->
<template>
  <div>
    <h1>Blog Posts</h1>
    
    <select v-model="selectedCategory" @change="filterPosts">
      <option value="">All Categories</option>
      <option v-for="category in categories" :key="category" :value="category">
        {{ category }}
      </option>
    </select>
    
    <div v-for="post in filteredPosts" :key="post.documentId" class="blog-post">
      <h2>{{ post.Title }}</h2>
      <p>Author: {{ post.Author }}</p>
      <p>{{ post.snippet }}</p>
       
      <!-- USE DOCUMENTID HERE -->
      <NuxtLink :to="`/blog/${post.documentId}`" class="read-more">
        Read More
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
const { data: posts } = await $fetch('http://localhost:1337/api/blog-posts')

const allPosts = ref(posts)
const filteredPosts = ref(posts)
const selectedCategory = ref('')

const categories = computed(() => {
  return [...new Set(allPosts.value.map(post => post.Category))]
})

function filterPosts() {
  if (selectedCategory.value) {
    filteredPosts.value = allPosts.value.filter(
      post => post.Category === selectedCategory.value
    )
  } else {
    filteredPosts.value = allPosts.value
  }
}
</script>



<style scoped>
@import '~/css/index.css';
</style>