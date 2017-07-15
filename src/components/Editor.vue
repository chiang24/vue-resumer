<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active:currentTab === i}" v-on:click="currentTab = i">
                    <svg class="icon">
                        <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>
                </li>
                <!-- <li v-bind:class="{active:currentTab === 0}" v-on:click="currentTab = 0">
                            <svg class="icon" aria-hidden="true">
                            <use xlink:href="#icon-shenfenzheng"></use>
                            </svg>
                        </li>
                        <li v-bind:class="{active:currentTab === 1}" v-on:click="currentTab = 1">
                            <svg class="icon" aria-hidden="true">
                            <use xlink:href="#icon-work"></use>
                            </svg>
                        </li>
                        <li v-bind:class="{active:currentTab === 2}" v-on:click="currentTab = 2">
                            <svg class="icon" aria-hidden="true">
                            <use xlink:href="#icon-book"></use>
                            </svg>
                        </li>
                        <li v-bind:class="{active:currentTab === 3}" v-on:click="currentTab = 3">
                            <svg class="icon" aria-hidden="true">
                            <use xlink:href="#icon-xiangmu"></use>
                            </svg>
                        </li>
                        <li v-bind:class="{active:currentTab === 4}" v-on:click="currentTab = 4">
                            <svg class="icon" aria-hidden="true">
                            <use xlink:href="#icon-jiangbei"></use>
                            </svg>
                        </li>
                        <li v-bind:class="{active:currentTab === 5}" v-on:click="currentTab = 5">
                            <svg class="icon" aria-hidden="true">
                            <use xlink:href="#icon-phone"></use>
                            </svg>
                        </li> -->
            </ol>
        </nav>
        <ol class="panes">
            <!-- <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}" >
                    Tab {{i+1}}
                    </li> -->
            <li v-bind:class="{active:currentTab === 0}">
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
            </li>
            <li v-bind:class="{active:currentTab === 1}">
                <h2>工作经历</h2>
                <el-form class="workInput">
                    <div v-for="(work,index) in workHistory" class="workBlock">
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
                    <el-button class="btn" type="text"  v-on:click="addWorkHistory">+ 添加更多</el-button>
                </el-form>
            </li>
            <li v-bind:class="{active:currentTab === 2}">
                <h2>学习经历</h2>
            </li>
            <li v-bind:class="{active:currentTab === 3}">
                <h2>项目经历</h2>
            </li>
            <li v-bind:class="{active:currentTab === 4}">
                <h2>获奖情况</h2>
            </li>
            <li v-bind:class="{active:currentTab === 5}">
                <h2>联系方式</h2>
            </li>
        </ol>
    </div>
</template>

<script>
export default {
    data() {
        return {
            currentTab: 0,
            icons: ['shenfenzheng', 'work', 'book', 'xiangmu', 'jiangbei', 'phone'],
            profile: {
                name: '',
                city: '',
                birth: '',
                job: '',
                introduction: ''
            },
            workHistory: [
                {
                    company: '',
                    content: '',
                    post: ''
                }
            ]
        }
    },
    methods: {
        addWorkHistory() {
            this.workHistory.push(
                {
                    company: '',
                    content: '',
                    post: ''
                })
        },
        removeWorkHistory(index) {
            this.workHistory.splice(index, 1)
        }
    },
    created() {
    }
}
</script>

<style lang="scss">
#editor {
    color: #333;
    min-height: 100px;
    display: flex;
    background: white;
    >nav {
        background: #192229;
        width: 80px;
        text-align: center;
        >ol li {
            padding-top: 16px;
            padding-bottom: 16px;
            >.icon {
                width: 32px;
                height: 32px;
                fill: white;
            }
            &.active {
                background: white;
                >.icon {
                    fill: #192229;
                }
            }
        }
    }
    >.panes {
        >li {
            display: none;
            overflow: auto;
            height: 100%;
            &.active {
                display: block;
            }
            >h2 {
                color: #192229;
                padding-top: 20px;
                padding-left: 32px;
                box-sizing: border-box;
            }
            >.profileInput {
                width: 415px;
                padding: 12px 32px 32px 32px;
            }
            >.workInput {
                width: 390px;
                padding: 20px 32px 32px 32px;
                position: relative;
                >div {
                    margin-bottom: 20px;
                    box-shadow: 0 0 3px hsla(0, 0, 0, 0.3);
                    padding: 16px 16px;
                    position: relative;
                    >.el-icon-circle-cross {
                    position: absolute;
                    right: 16px;
                    top: 16px;
                    z-index: 10;
                    }
                }
                > .btn{
                      position: absolute;
                       right: 32px;
                       bottom:7px;
                       left: 50%;
                       margin-left: -34px;
                    }
            }
        }
    }
}
</style>

