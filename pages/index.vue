<template>
  <div class="page-index">
    <el-row>
      <el-col :span="5">
        <my-menu />
      </el-col>
      <el-col :span="19">
        <life />
      </el-col>
    </el-row>
    <el-row :span="24">
      <artistic />
    </el-row>
  </div>
</template>

<script>
  import MyMenu from '@/components/index/menu.vue'
  import Life from '@/components/index/life.vue'
  import Artistic from '@/components/index/artistic.vue'
  export default{
    components:{
      MyMenu,
      Life,
      Artistic
    }
  }
</script>

<style lang="scss">
@import "@/assets/css/index/index.scss";
</style>
