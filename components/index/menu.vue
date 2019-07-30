<template>
  <div class="m-menu">
    <dl class="nav" @mouseleave="onMouseleave">
      <dt>全部分类</dt>
      <dd v-for="(item,index) in menu" :key="index" @mouseenter="onmouseenter">
        <i :class="item.type"/>{{item.name}}<span class="arrow"/>
      </dd>
    </dl>
    <div class="detail" v-if="kind" @mouseenter="senter" @mouseleave="sleave">
      <template v-for="item in curDetail.child">
        <h4>{{item.title}}</h4>
        <span v-for="val in item.child" :key="val">{{val}}</span>
      </template>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
      //鼠标滑过选中的列表
        kind: '',
        menu: [{
          type: 'food',
          name: '美食',
          child: [{
            title: '美食',
            child: ['代金券', '甜点饮品', '火锅', '自助餐', '小吃快餐']
          }]
        }, {
          type: 'takeout',
          name: '外卖',
          child: [{
            title: '外卖',
            child: ['美团外卖']
          }]
        }, {
          type: 'hotel',
          name: '酒店',
          child: [{
            title: '酒店星级',
            child: ['经济型', '舒适/三星', '高档/四星', '豪华/五星']
          }]
        }]
      }
    },
    computed: {
      curDetail() {
        return this.menu.filter(item=>{return item.type==this.kind})[0];
      }
    },
    methods: {
      //鼠标离开nav
      onMouseleave() {
        this.timer = setTimeout(()=>{
          this.kind = '';
        },150);
      },
      // 鼠标进入nav
      onmouseenter(e) {
        this.kind = e.target.querySelector('i').className;
      },
      senter() {
        clearTimeout(this.timer);
      },
      sleave() {
        this.kind = '';
      }
    }
  }
</script>

<style lang="scss">

</style>
