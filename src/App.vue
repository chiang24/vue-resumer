<template>
  <div id="app" v-bind:class="{previewMode:previewMode}">
      <div class="dialogWrapper">
          <Topbar class="topbar"  v-on:preview="preview"/>
    <main>
    <Editor v-bind:resume="resume" class="editor"/>
    <Preview v-bind:resume="resume" class="preview"/>
    </main>
      </div>
    
    <el-button id="exitPreview"type="primary" v-on:click="exitPreview">退出预览</el-button>
  </div>
</template>

<script>

  import Topbar from './components/Topbar'
  import Editor from './components/Editor'
  import Preview from './components/Preview'

  export default {
    data(){
      return{
        previewMode:false,
        resume:{
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
                
            ],
            ProjectsHistory:[
                {
                    projectName: '',
                    responsibilities: '',
                    useTime: '',
                    projectIntroduction: ''
                }
            ],
            HonorsHistory:[
                {
                    awards:'',
                    honorDate:''
                }
            ],
            ContactInformation:
                {
                    phone:'',
                    email:'',
                    blog:''
                }
            
        }
      }
    },

  components: {
   Topbar,Editor,Preview
  },
    methods:{
        preview(){
            this.previewMode = true
        },
        exitPreview(){
            this.previewMode = false
        }
    }
}
</script>

<style lang="scss">
html,body,#app{
  height: 100%;     /* 需要给它以及body、html都要100%,等价于100vh */
  overflow: hidden;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
}
.topbar{
  position: relative;
  background-color: #407FE3;
  box-shadow: 0 0 3px hsla(0,0,0,0.5);
}
.icon {
       width: 1em; height: 1em;
       vertical-align: -0.15em;
       fill: currentColor;
       overflow: hidden;
}
.dialogWrapper{
    height: 100vh;
    display: flex;
    flex-direction: column;
    background: #EAEBEC;
> main{
  display: flex;
  flex: 1;
  background: #F0F0F0;
   > .editor{
    width: 40em;
    margin: 16px 8px 16px 16px;
    box-shadow: 0 0 3px hsla(0,0,0,0.5);
    border-radius: 4px;
    overflow: auto;
  }
  
  > .preview{
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: white;
    box-shadow: 0 0 3px hsla(0,0,0,0.5);
    border-radius: 4px;
    overflow: auto;
  }
}
}

.previewMode  #topbar{
  display: none;
}
.previewMode #editor{
  display: none;
}
.previewMode #preview{
  max-width: 800px;
  margin: 32px auto;
}
#exitPreview{
  display: none;
}
.previewMode #exitPreview{
  display: inline-block;
  position: fixed;
  right: 16px;
  bottom: 16px;
}
</style>
