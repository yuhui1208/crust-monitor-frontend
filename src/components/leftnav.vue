/**
* 左边菜单
*/ 
<template>
  <el-menu default-active="2" :collapse="collapsed" collapse-transition router :default-active="$route.path" unique-opened class="el-menu-vertical-demo" background-color="#334157" text-color="#fff" active-text-color="#ffd04b">
    <div class="logobox">
      <img class="logoimg" src="../assets/img/logo.png" alt="">
    </div>
    <el-submenu v-for="menu in allmenu" :key="menu.menuid" :index="menu.menuname">
      <template slot="title">
        <i class="iconfont" :class="menu.icon"></i>
        <span>{{menu.menuname}}</span>
      </template>
      <el-menu-item-group>
        <el-menu-item v-for="chmenu in menu.menus" :index="'/'+chmenu.url" :key="chmenu.menuid">
          <i class="iconfont" :class="chmenu.icon"></i>
          <span>{{chmenu.menuname}}</span>
        </el-menu-item>
      </el-menu-item-group>
    </el-submenu>
  </el-menu>
</template>
<script>

export default {
  name: 'leftnav',
  data() {
    return {
      collapsed: false,
      allmenu: []
    }
  },
  created() {
    let res = {
      success: true,
      data: [
        {
          menuid: 1,
          icon: 'li-icon-xiangmuguanli',
          menuname: '基础管理',
          hasThird: null,
          url: null,
          menus: [
            {
              menuid: 666,
              icon: 'icon-cat-skuQuery',
              menuname: '存储市场概览',
              hasThird: 'N',
              url: 'market/StorageMarketOverview',
              menus: null
            },
            {
              menuid: 113,
              icon: 'icon-cat-skuQuery',
              menuname: 'slot查询上报详情',
              hasThird: 'N',
              url: 'swork/ReportedStatusBySlot',
              menus: null
            },
            {
              menuid: 132,
              icon: 'icon-cat-skuQuery',
              menuname: '文件总览',
              hasThird: 'N',
              url: 'market/FileOverview',
              menus: null
            },
            {
              menuid: 352,
              icon: 'icon-cat-skuQuery',
              menuname: '文件大小分布',
              hasThird: 'N',
              url: 'market/FileSizeOverview',
              menus: null
            },
            {
              menuid: 782,
              icon: 'icon-cat-skuQuery',
              menuname: '文件份数分布',
              hasThird: 'N',
              url: 'market/FileCountOverview',
              menus: null
            },
            {
              menuid: 783,
              icon: 'icon-cat-skuQuery',
              menuname: '商户Staked文件',
              hasThird: 'N',
              url: 'market/MerchantStakedInfo',
              menus: null
            },
            {
              menuid: 784,
              icon: 'icon-cat-skuQuery',
              menuname: '文件价格',
              hasThird: 'N',
              url: 'market/FilePrice',
              menus: null
            },
            {
              menuid: 785,
              icon: 'icon-cat-skuQuery',
              menuname: 'group总览',
              hasThird: 'N',
              url: 'swork/GroupFiles',
              menus: null
            }
          ]
        }
      ],
      msg: 'success'
    }
          this.allmenu = res.data
    
    // menu(localStorage.getItem('logintoken'))
    //   .then(res => {
    //     console.log(JSON.stringify(res))
    //     if (res.success) {
    //       this.allmenu = res.data
    //     } else {
    //       this.$message.error(res.msg)
    //       return false
    //     }
    //   })
    //   .catch(err => {
    //     this.$message.error('菜单加载失败，请稍后再试！')
    //   })
    // 监听
    this.$root.Bus.$on('toggle', value => {
      this.collapsed = !value
    })
  }
}
</script>
<style>
.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 240px;
  min-height: 400px;
}
.el-menu-vertical-demo:not(.el-menu--collapse) {
  border: none;
  text-align: left;
}
.el-menu-item-group__title {
  padding: 0px;
}
.el-menu-bg {
  background-color: #1f2d3d !important;
}
.el-menu {
  border: none;
}
.logobox {
  height: 40px;
  line-height: 40px;
  color: #9d9d9d;
  font-size: 20px;
  text-align: center;
  padding: 20px 0px;
}
.logoimg {
  height: 40px;
}
</style>