<template>
    <div>
        <h2>工作经历</h2>
        <el-form class="workInput">
            <div v-for="(work,index) in WorkHistory" class="workBlock">
                <i class="el-icon-circle-cross" v-on:click="removeWorkHistory(index)"></i>
                <el-form-item label="公司名称">
                    <el-input v-model="work.company" placeholder="公司名称"></el-input>
                </el-form-item>
                <el-form-item label="职位">
                    <el-input v-model="work.post" placeholder="职位"></el-input>
                </el-form-item>
                <el-form-item label="工作内容" prop="desc">
                    <el-input type="textarea" :autosize="{ minRows: 3, maxRows: 6}" placeholder="工作内容" v-model="work.content">
                    </el-input>
                </el-form-item>
            </div>
            <el-button class="btn" type="text" v-on:click="addWorkHistory">+ 添加更多</el-button>
        </el-form>
    </div>
</template>
<script>
export default {
  props:['WorkHistory'],
  methods: {
        addWorkHistory() {
            this.WorkHistory.push(
                {
                    company: '',
                    content: '',
                    post: ''
                })
        },
        removeWorkHistory(index) {
            this.WorkHistory.splice(index, 1)
        }
    }
}
</script>
