<template>
  <div class="home">
    <Header @searchByTerm="searchByTerm" />

    <div class="home__container">
      <home-list v-if="!term && links" :dataList="links"></home-list>
      <home-list v-if="term && resultList.length > 0" :dataList="resultList"></home-list>
      <p v-if="term && resultList.length == 0" class="home__no-results">Sem Resultados, refaça sua busca</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/header/Header';
import HomeList from './components/HomeList/HomeList';

export default {
  name: 'Home',

  components: {
    Header,
    HomeList,
  },

  mounted() {
    // this.getData();

    this.newList = this.list;
  },

  data() {
    return {
      baseUrl: process.env.VUE_APP_BASE_URL,
      term: '',
      resultList: [],
      links: [
        {
          meta: {
            author: 'Danil Ishutin',
            title: 'Font Size Idea: px at Root, rem for Components, em for Text Elements',
            url: 'css-tricks.com'
          },
          category: 'ux_ui',
          comments: 7,
          created_at: 1459857600,
          upvotes: 9
        },
        {
          meta: {
            author: 'Christopher Alesund',
            title: 'Case study: Redesigning the Folyo landing page',
            url: 'medium.com'
          },
          category: 'case_study',
          comments: 0,
          created_at: 1460289600,
          upvotes: 2
        },
        {
          meta: {
            author: 'Olof Kajbjer',
            title: 'Want people to use your product? Use it yourself',
            url: 'medium.com'
          },
          category: 'product_design',
          comments: 4,
          created_at: 1460030400,
          upvotes: 11
        },
        {
          meta: {
            author: 'Mikael Greif',
            title: 'What do you do with a failed project?',
            url: 'mika.el'
          },
          category: 'discussion',
          comments: 2,
          created_at: 1460203200,
          upvotes: 4
        },
        {
          meta: {
            author: 'Kenny Schrub',
            title: 'Some things cant be prototyped',
            url: 'mika.el'
          },
          category: 'discussion',
          comments: 25,
          created_at: 1460203200,
          isOwner: true,
          upvotes: 4
        },
        {
          meta: {
            author: 'Pasha Biceps',
            title: 'Dont let bad process or structure kill great interfaces',
            url: 'medium.com'
          },
          category: 'product_design',
          comments: 0,
          created_at: 1460376000,
          isOwner: true,
          upvotes: 2
        },
        {
          meta: {
            author: 'Jacky Mao',
            title: 'How to prototype without any tools',
            url: 'jackymao.wix'
          },
          caegory: 'product_design',
          coments: 0,
          upvotes: 1
        }  
      ]
    };
  },


  methods: {
    searchByTerm(searchTerm) {
      this.term = searchTerm;

      this.resultList = this.links.filter(item => item.category === this.term || item.meta.url === this.term || item.meta.author === this.term);


    }

  },
};
</script>


<style lang='stylus' src='./Home.styl' scoped />
