<template>
    <div>
        <h2>项目经历</h2>
        <el-form class="projectsInput" :label-position="labelPosition">
            <div v-for="(projects,index) in ProjectsHistory" class="ProjectsBlock">
                <i class="el-icon-circle-cross" v-on:click="removeProjectsHistory(index)"></i>
                <el-form-item label="项目名称">
                    <el-input v-model="projects.projectName" placeholder="项目名称"></el-input>
                </el-form-item>
                <el-form-item label="你的职责">
                    <el-input v-model="projects.responsibilities" placeholder="职责"></el-input>
                </el-form-item>
                <el-form-item label="项目起止时间">
                    <el-col>
                        <el-date-picker v-model="projects.useTime" type="daterange" placeholder="选择日期范围"></el-date-picker>
                    </el-col>
                </el-form-item>
                <el-form-item label="项目介绍" prop="desc">
                <el-input type="textarea" :autosize="{ minRows: 3, maxRows: 6}" placeholder="项目介绍" v-model="projects.projectIntroduction"></el-input>
                </el-form-item>
            </div>
            <el-button class="btn" type="text" v-on:click="addProjectsHistory">+ 添加更多</el-button>
        </el-form>
    </div>
</template>
<script>
export default {
    props: ['ProjectsHistory'],
    methods: {
        addProjectsHistory() {
            this.ProjectsHistory.push(
                {
                    projectName: '',
                    responsibilities: '',
                    useTime: '',
                    projectIntroduction: ''
                })
        },
        removeProjectsHistory(index) {
            this.ProjectsHistory.splice(index, 1)
        }
    },
    data() {
        return {
            pickerOptions0: {
                disabledDate(time) {
                    return time.getTime() < Date.now() - 8.64e7;
                }
            },
            labelPosition: 'top'
        }
    }
}
</script>
