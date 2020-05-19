<template>
  <div>
    <!-- <h1>{{ $route.params.slug }}</h1> -->
    <h1>{{ article1_title }}</h1>

    <img  
      v-if="article1_img"
      :src="article1_img"
      alt=""
    >
    <img
      v-else
      src="http://via.placeholder.com/250x250"
      alt=""
    >
    <span>Le {{ article1_author }}</span>
    <span>Par {{ article1_date }}</span>
    <p>{{ article1_desc }}</p>
  </div>
</template>

<script>
export default {
  name: 'Article',
  data() {
    return {
    }
  },
}
</script>