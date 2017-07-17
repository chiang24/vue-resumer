<template>
<div id="topbar" v-on:preview="preview">
    <h1 class="title">Resumer</h1>
    <div>
    <el-button type="primary">注册</el-button>
    <el-button >登陆</el-button>
    <el-button v-on:click="preview">预览</el-button>
    </div> 

</div>
</template>
<script>
export default {
  methods:{
      preview(){
        this.$emit('preview')
      }
  }
}
</script>


<style lang="scss">
#topbar{
color:white;
min-height: 80px;
display: flex;
align-items: center;
justify-content: space-between;
padding-left: 104px;
padding-right: 104px;
}
</style>
