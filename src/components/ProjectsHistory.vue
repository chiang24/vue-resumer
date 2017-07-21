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
                    <el-form-item label="项目开始时间">
                    <div class="block">
                        <el-date-picker v-model="projects.beginTime" type="date" placeholder="选择开始时间" :picker-options="pickerOptions0"></el-date-picker>
                    </div>
                </el-form-item>
                <el-form-item label="项目结束时间">
                    <div class="block">
                        <el-date-picker v-model="projects.endTime" type="date" placeholder="选择结束时间" :picker-options="pickerOptions0"></el-date-picker>
                    </div>
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
                    beginTime: '',
                    endTime:'',
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
