<template>
  <div class="home-list">
    <div class="home-list__item" v-for="(item, index) in dataList" :key="index">
      <div class="home-list__item-position">
        <div class="home-list__item-position__arrow">ˆ</div>
        <div class="home-list__item-position__number">12</div>
      </div>
      <div class="home-list__box-info">
        <h3 class="home-list__box-info__site">{{item.meta.url}}</h3>
        <h2 class="home-list__box-info__title">{{item.meta.title}}</h2>
        <div class="home-list__box-info__bar">
          <div
            v-if="item.category" 
            :class="[`badge badge-${item.category}`]">
            {{item.category}}
          </div>
          <div class="home-list__box-info__bar__box-user">
            <img src="https://via.placeholder.com/30" class="box-user__image" />
            <h4 class="box-user__name">{{item.meta.author}}</h4>
          </div>
          <div class="home-list__box-info__bar-time"> minutes</div>
          <div class="home-list__box-info__bar__coments">
            <span class="home-list__box-info__bar__coments-number">{{item.comments}}</span>
            <span>coments</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import moment from 'moment'
export default {
  name: "HomeList",

    props: {
      dataList: { type: Array, default: () => [] },
    },

  data() {
    return {
      listPosts: [],
    };
  },

  mounted() {
    this.getData();
  },

  methods: {
    secundecondsToMinutes() {



    },

    getData() {
      axios
        .get(
          "https://raw.githubusercontent.com/deblynprado/frontend-test/master/instructions/data.json"
        )
        .then(response => {
          console.log(response.data);
          this.listPosts = response.data;
        });
    }
  }
};
</script>


<style lang='stylus' src='./HomeList.styl' scoped />