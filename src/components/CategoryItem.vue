<template>
  <li>
    <div class="category-header" @click="toggle">
      <img
        v-if="category.fileUrlSmall"
        :src="category.fileUrlSmall"
        alt="Category Image"
        class="category-image"
      />
      <h2>{{ category.name }}</h2>
    </div>
    <ul v-if="isOpen && category.children && category.children.length">
      <li v-for="child in category.children" :key="child.id">
        <CategoryItem :category="child" />
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  name: 'CategoryItem',
  props: {
    category: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    toggle() {
      this.isOpen = !this.isOpen;
    }
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  font-size: 50px;
}

.category-header {
  cursor: pointer;
  display: flex;
  align-items: center;
  padding: 10px;
  background-color: #f0f0f0;
  margin-bottom: 5px;
  font-size:10px;
}

.category-header h2 {
  margin: 0;
  flex: 1; 
}

.category-image {
  width: 20px;
  height: 20px;
  object-fit: contain;
  margin-right: 10px; 
}
</style>
