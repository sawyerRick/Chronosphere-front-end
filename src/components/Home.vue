<template>
  <div>
    <el-container>
      <el-header>
        <el-menu :default-active="currComponent" class="el-menu-demo" mode="horizontal" @select="handleSelect">
          <el-menu-item index="Chronosphere">Chronosphere</el-menu-item>
          <el-menu-item index="Upload">上传</el-menu-item>
          <el-menu-item index="Create">创建</el-menu-item>
          <el-menu-item index="My">我的</el-menu-item>
          <el-menu-item index="About">关于</el-menu-item>
          <el-menu-item disabled index="userPlaceHolder">{{userPlaceHolder}}</el-menu-item>
        </el-menu>
      </el-header>
      <el-main>
        <!-- 动态组件 -->
        <div v-bind:is="currComponent"></div>
      </el-main>
    </el-container>
  </div>
</template>

<script>
  import Chronosphere from './Chronosphere.vue'
  import Upload from './Upload.vue'
  import My from './My.vue'
  import About from './About.vue'
  import Create from './Create.vue'
  
  export default {
    components: {
      Chronosphere,
      My,
      Upload,
      About,
      Create
    },
    data() {
      return {
        currComponent: "Chronosphere",
        userPlaceHolder: "未登录"
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log("curr component:" + key);
        this.currComponent = key;
      }
    }
  }
</script>


<style>
  .el-header, .el-footer {
    /* background-color: #B3C0D1; */
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  
  body > .el-container {
    margin-bottom: 40px;
  }
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }

</style>