<!-- u24673898 Franky -->
 <!-- test -->
<template>
  <div>
    <h1>Search</h1>
    <input 
      v-model="searchQuery" 
      placeholder="Search posts or authors..." 
      @input="search"
    >
    
    <div v-for="post in searchResults" :key="post.slug" class="search-result">
      <h3>
        <NuxtLink :to="`/blog/${post.documentId}`">
          {{ post.Title }}
        </NuxtLink>
      </h3>
      <p>Author: {{ post.Author }}</p>
    </div>
  </div>
</template>

<script setup>
const searchQuery = ref('')
const searchResults = ref([])

async function search() {
  if (searchQuery.value.length > 2) {
    const { data } = await $fetch(`http://localhost:1337/api/blog-posts?filters[$or][0][Title][$contains]=${searchQuery.value}&filters[$or][1][Author][$contains]=${searchQuery.value}`)
    searchResults.value = data
  } else {
    searchResults.value = []
  }
}
</script>
<style scoped>
@import '~/css/search.css';
</style>