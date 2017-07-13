<template>
<div id="editorText">
    <nav>
        <ol>
            <li v-bind:class="{active:currentTab === 0}" v-on:click="currentTab = 0">
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
            </li>
        </ol>
    </nav>
    <ol class="panes">
        <li v-bind:class="{active:currentTab === 0}">Tab1</li>
        <li v-bind:class="{active:currentTab === 1}">Tab2</li>
        <li v-bind:class="{active:currentTab === 2}">Tab3</li>
        <li v-bind:class="{active:currentTab === 3}">Tab4</li>
        <li v-bind:class="{active:currentTab === 4}">Tab5</li>
        <li v-bind:class="{active:currentTab === 5}">Tab6</li>
    </ol>
</div>
</template>

<<script>
export default {
  data(){
      return {
         currentTab: 0,
      }
  }
}
</script>
>

<style lang="scss">
#editorText{
color:green;
min-height: 100px;
display: flex;
background: white;
 > nav{
    background: #192229;
    width: 80px;
    text-align: center;
    > ol li{
     padding-top:16px;
     padding-bottom: 16px;
     > .icon{
     width:32px;
     height: 32px;
     fill:white;
 }
     &.active{
     background: white;
     > .icon{
         fill: black;
     }
 }
 }
 }
 > .panes{
     > li {display: none;
     &.active{
         display: block;
     }
 }
 }
}
</style>

