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
               <ProfileEditor v-bind:profile="profile"/>
            </li>
            <li v-bind:class="{active:currentTab === 1}">
                <WorkHistory v-bind:WorkHistory="WorkHistory"/>
            </li>
            <li v-bind:class="{active:currentTab === 2}">
                <StudyHistory v-bind:StudyHistory="StudyHistory"/>
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
import ProfileEditor from './ProfileEditor.vue'
import WorkHistory from './WorkHistory.vue'
import StudyHistory from './StudyHistory.vue'
export default {
    components:{ProfileEditor,WorkHistory,StudyHistory},
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
            WorkHistory: [
                {
                    company: '',
                    content: '',
                    post: ''
                }
            ],
            StudyHistory:[
                {
                    school:'',
                    profession:'',
                    education:['大专','本科','硕士','博士','其它'],
                    graduation:''   
                }
                
            ]
        }
    },
    methods: {
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
            >div h2 {
                color: #192229;
                padding-top: 20px;
                padding-left: 32px;
                box-sizing: border-box;
            }
            >div .profileInput {
                width: 415px;
                padding: 12px 32px 32px 32px;
            }
            >div .workInput {
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
            >div .studyInput {
                width: 390px;
                padding: 20px 32px 32px 32px;
                position: relative;
                >div {
                    margin-bottom: 20px;
                    box-shadow: 0 0 3px hsla(0, 0, 0, 0.3);
                    padding: 30px 16px;
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

