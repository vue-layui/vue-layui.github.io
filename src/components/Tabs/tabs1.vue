<template>
  <div id="app" class="box">
  <ul class="tabs clearfix">
    <li v-for="(tab,index) in tabsName">
      <a href="javascript:;" rel="external nofollow" class="tab-link" @click="tabsSwitch(index)" v-bind:class="{active:tab.isActive}">{{tab.name}}</a>
    </li>
  </ul>
  <div class="cards">
    <div class="tab-card" style="display: block;">这里是HTML教程</div>
    <div class="tab-card">欢迎来到CSS模块</div>
    <div class="tab-card">嗨，这里是Vue</div>
  </div>
</div>
</template>

<script>
    export default {
      name: "tabs1",
      data() {
        return {
          tabsName: [{
            name: "HTML",
            isActive: true
          }, {
            name: "CSS",
            isActive: false
          }, {
            name: "Vue",
            isActive: false
          }],
          active: false
        }
      },
      methods: {
        tabsSwitch: function(tabIndex) {
          var tabCardCollection = document.querySelectorAll(".tab-card"),
            len = tabCardCollection.length;
          for(var i = 0; i < len; i++) {
            tabCardCollection[i].style.display = "none";
            this.tabsName[i].isActive = false;
          }
          this.tabsName[tabIndex].isActive = true;
          tabCardCollection[tabIndex].style.display = "block";
        }
      }
    }
</script>

<style scoped>
  * {
    padding: 0;
    margin: 0;
  }
  .box {
    width: 70%;
    height: 200px;
    /*margin: 0 auto;*/
    border: 1px solid #000;
  }
  .tabs{
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
  .tabs li {
    width: 100%;
    float: left;
    margin-right: 8px;
    list-style: none;
  }
  .tabs .tab-link {
    display: block;
    width: 104%;
    height: 49px;
    text-align: center;
    line-height: 49px;
    background-color: #5597B4;
    color: #fff;
    text-decoration: none;
  }
  .tabs .tab-link.active {
    height: 47px;
    border-bottom: 2px solid #E35885;
    transition: .3s;
    /*transform: scale(1.2);*/
    background-color: midnightblue;
  }
  .cards {
    float: left;
  }
  .cards .tab-card {
    display: none;
  }
  .clearfix:after {
    content: "";
    display: block;
    height: 0;
    clear: both;
  }
  .clearfix {
    zoom: 1;
  }
</style>
