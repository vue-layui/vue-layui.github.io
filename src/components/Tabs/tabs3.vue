<template>
  <div id="app2">
    <div class="menuList">
      <ul>
        <li v-for="(item,index) in list" :key="item.id" :class="{active:num==index}" @click="getNum(index)">
          {{item}}
        </li>
      </ul>
    </div>
    <div class="tabCon">
      <div v-for='(itemCon,index) in tabContents' v-show="index == num">
        {{itemCon}}
      </div>
    </div>
  </div>
</template>

<script>
    export default {
      name: "tabs3",
      data() {
        return {
          num: 0,
          list: ["张三丰", "独孤求败", "周伯通"],
          tabContents: [
            "张三丰，名君宝，字符元，道号三丰。武林至尊，民族英雄 、内拳始祖、太极始祖、武学泰斗、龙行书法始祖张三丰集各派绝学于一身，威震武林，造诣已达炼虚合道至高极境 [1] ，元末明初真人，武当山道人，武当派始祖，正史记载宋理宗淳佑七年(1247年) 出生辽东，14岁考取文武状元，18岁担任博陵县令，（1280年）辞官出家修道，拜火龙真人为师，武林盟主张三丰时隐时现，至今行踪不定，清朝道光年间曾出现在峨眉山。",
            "独孤求败，自号“剑魔”，纵横江湖三十馀载，杀尽仇寇，败尽英雄，天下更无抗手，无可奈何，惟隐居深谷，以雕为友。呜呼，生平求一敌手而不可得，诚寂寥难堪也。在小说中从未出场过，只曾在人物的口中提及。",
            "周伯通不是金大师小说中的主角，也不是塑造的最丰满、最完善的形象，更不是侠客或英雄的代表，而且就武侠小说最基本的要素-武功、武学所达到的境界来说，周伯通也不是绝顶高手，但毫无疑问，周伯通是金大师所塑造的所有人物中最有意思的一位，至少是最有意思的人物之一。"],
        }
      },
      methods: {
        getNum(index) {
          this.num = index;
        }
      }

    }
</script>

<style scoped>
  html,
  body {
    margin: 0;
    padding: 0;
    background-color: #58596b;
  }
  .active {
    color: #fff;
    background: #e74c3c;
  }
  #app2 {
    width: 70%;
    height: 300px;
    background-color: #fff;
    box-shadow: 0 1px 3px rgba(0, 0, 0, .1);
    /*margin-top:200px;*/
  }
  .menuList {
    width: 100%;
    height: 60px;
    background-color: #33344a;
  }
  ul {
    width: 100%;
    display: flex;
    list-style: none;
    padding: 0;
    margin: 0;
    color: #717181;
    font-size: 16px;
    line-height: 60px;
  }
  ul li {
    flex: 1;
    text-align: center;
    cursor: pointer;
  }
  .tabCon {
    width: 90%;
    margin: 0 auto;
    padding: 40px 20px;
    color: #999;
    font-size: 14px;
    background-color: #fff;
  }
</style>
