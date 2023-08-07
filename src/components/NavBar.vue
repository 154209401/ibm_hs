<template>
<div class="back-pc">
<div class="TopImg">
</div>
<div style="margin:0 auto;width:100%;">
  <div class="TabLand">
<a-menu
    id="dddddd"   
    style="background-color:transparent;lineHeight: 4.24vh;height:4.24vh"
    mode="horizontal"
  >
 
 <template v-for="item in list">
        <!-- 如果当前遍历项没有children，视为子菜单项，注意所有的key都是path用于路由跳转，以及当前选中记录 -->
        <a-menu-item v-if="item" :key="item.key" :class="{selected: selectedTag == item.key}" @click="change(item.key)">
          <router-link :to="item.path">{{ item.title }}</router-link>
        </a-menu-item>
    </template>
    
  </a-menu>
  </div>
</div>
</div>
</template>

<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({
  computed:{
    menuRoutes(){
      return this.$router.options.routes[0].children
    }
  },
  data(){

    return{
      
         list: [
        {
          key: '1',
          title: 'QualityPredict',
          path: '/home/QualityPredict'
        },
        {
          key: '2',
          title: 'QualitySolution',
          path: '/home/QualitySolution'
        },
        {
          key: '3',
          title: 'InfoPlatform',
          path: '/home/InfoPlatform'
        },
      ],
       selectedTag: '1'
    }
  },
  methods:{
      change(tag: string){
      this.selectedTag = tag
    },
  },
  
  mounted() {
    this.$router.push('/home/QualityPredict')
  },
  
  

})
</script>

<style scoped>
/deep/  .ant-menu-horizontal >  .ant-menu-item.selected a {
  color: #d4ba71;
}
/deep/ .ant-menu-horizontal > .ant-menu-item a:hover {
  color: #d4ba71;
}
.ant-menu-horizontal {
  border-bottom: none;
}
/deep/ .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu { 
  width: 7.8125vw;
  height: 4.24vh;
}
/deep/ .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu:hover {
  border:0px;
}
.TabLand {
  margin:0 auto;
  width: 32vw;
  height: 8vh;
 background: url('../assets/imgs/Tabbg.png') no-repeat;
  background-size: 100% 65%;
  padding-left: 4.5vw;
    margin-bottom:-0.9vh;
}
.ant-menu-horizontal > .ant-menu-item a {
  color:#6cefc6;
}
.TopImg{
  width: 100%;
  height:8vh;
  margin: 0 auto;
   margin-top: 0.925vh;
  background: url('../assets/imgs/biaoti.png') no-repeat;
  background-size: 100% 100%;
    margin-bottom:10px;
}
/deep/ .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item:hover::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu:hover::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item-active::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu-active::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item-open::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu-open::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item-selected::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu-selected::after {
    border-bottom: 0px!important;
}
/deep/ .ant-menu-item-selected {
  border:0px!important;
}
/deep/ .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item:hover::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu:hover::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item-active::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu-active::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item-open::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu-open::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item-selected::after, .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-submenu-selected::after {
    border-bottom: 0px!important;
}
/deep/ .ant-menu-horizontal:not(.ant-menu-dark) > .ant-menu-item-selected::after {
   border-bottom: 0px!important;
}
</style>