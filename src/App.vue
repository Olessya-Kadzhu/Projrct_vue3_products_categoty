<template>
  <div id="app">
<div class="container_category"> 
<h1 @click="toggleCategories">Категории</h1>
</div>
<div class="categories_items">
<ul v-if="isOpen">
      <li v-for="category in categories" :key="category.id">
        <CategoryItem :category="category" />
      </li>
    </ul>
</div>
  </div>
</template>

<script>
import CategoryItem from "./components/CategoryItem.vue"; 
import categoryData from "./category.json"; 

export default {
  name: "App",
  components: {
    CategoryItem,
  },
  data() {
    return {
      isOpen: false,
      categories: categoryData, 
    };
  },
  methods: {
    toggleCategories() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped>
h1{
    cursor: pointer;
}

#app{
  display: flex;
  flex-direction: row;
  width: 50%;
  font-size:10px;
}
li{
 list-style: none;
}


</style>
