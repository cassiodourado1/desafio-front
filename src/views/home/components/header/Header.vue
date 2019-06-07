<template>
<div class="header">
    <div class="header__container">
        <img src="https://via.placeholder.com/50" class="header__logo">
        <div class="header__search">
          <input 
            placeholder="Buscar" 
            type="search" 
            v-model="searchTerm" 
            class="header__search-input"
          />
          <button class="header__bar-icon" @click="searchByTerm">pesquisar</button>
        </div>
        <div class="header__search-bar"></div>
        <div class="header__actions-box"></div>
    </div>
</div>
</template>

<script>
export default {
    name: "Header",

    data() {
    return {
      searchTerm: '',
    };
  },

  methods: {
  searchByTerm() {
      this.$emit('searchByTerm', this.searchTerm);
    }
  }
};
</script>


<style lang='stylus' src='./Header.styl' scoped />
