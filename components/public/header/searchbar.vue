<template>
  <div class="search-panel">
    <el-row class="m-header-searchbar">
      <el-col
        :span="3"
        class="left">
        <img
          src="//s0.meituan.net/bs/fe-web-meituan/e5eeaef/img/logo.png"
          alt="美团">
      </el-col>
      <el-col
        :span="15"
        class="center">
        <div class="wrapper">
          <el-input v-model="inputData" @blur="onblur" @focus="onfocus" placeholder="搜索商家或地点"/>
          <button class="el-button el-button--primary"><i class="el-icon-search"/></button>
          <dl class="hotPlace" v-if="showHotPlace">
            <dt>热门搜索</dt>
            <dd v-for="(item,index) in hotPlace" :key="index">{{item}}</dd>
          </dl>
          <dl class="searchList" v-if="showSearchList">
            <dd v-for="(item,index) in searchList" :key="index">{{item}}</dd>
          </dl>
        </div>
        <p class="suggest">
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
        </p>
        <ul class="nav">
          <li>
            <nuxt-link
              to="/"
              class="takeout">美团外卖
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="movie">猫眼电影
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="hotel">美团酒店
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="apartment">民宿/公寓
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="business">商家入驻
            </nuxt-link>
          </li>
        </ul>
      </el-col>
      <el-col
        :span="6"
        class="right">
        <ul class="security">
          <li><i class="refund"/>
            <p class="txt">随时退</p></li>
          <li><i class="single"/>
            <p class="txt">不满意免单</p></li>
          <li><i class="overdue"/>
            <p class="txt">过期退</p></li>
        </ul>
      </el-col>
    </el-row>
  </div>
</template>

<script>

  export default {
    data() {
      return {
        //热门搜索与推荐搜索列表
        searchList: ['火锅','火锅','火锅'],
        hotPlace: ['故宫','故宫','故宫','故宫'],
        //输入框中的数据
        inputData: '',
        //输入框是聚焦还是失去焦点
        focus: false
      }
    },
    methods: {
      onblur() {
        setTimeout(()=>{
          this.focus = false;
        },200);
      },
      onfocus() {
        this.focus = true;
      }
    },
    computed: {
      showHotPlace() {
        return this.focus&&!this.inputData;
      },
      showSearchList() {
        return this.focus&&this.inputData;
      }
    }
  }
</script>

<style lang="scss">

</style>
