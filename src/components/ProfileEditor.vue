<template>
<div>
<h2>个人信息</h2>
    <el-form class="profileInput">
        <el-form-item label="姓名">
            <el-input v-model="profile.name" placeholder="姓名"></el-input>
        </el-form-item>
        <el-form-item label="所在城市">
            <el-input v-model="profile.city" placeholder="所在城市"></el-input>
        </el-form-item>
        <el-form-item label="出生年月">
            <el-input v-model="profile.birth" placeholder="出生年月"></el-input>
        </el-form-item>
        <el-form-item label="申请岗位">
            <el-input v-model="profile.job" placeholder="申请岗位"></el-input>
        </el-form-item>
        <el-form-item label="自我介绍" prop="desc">
            <el-input type="textarea" :autosize="{ minRows: 3, maxRows: 6}" placeholder="自我介绍" v-model="profile.introduction"></el-input>
        </el-form-item>
    </el-form>
</div>
</template>
<script>
export default {
  props:['profile']
}
</script>