<template>
 <div id="AppScore" class="row">
      <div class="form-group clearfix">
          <!-- <label class="control-label col-md-4">评分:{{starNum}}星</label> -->
          <div class="col-md-8">
              <div class="grade-box">
                  <img v-for="(star,index) in stars" :src="star.src" @click="rating(index)" alt="星星图片" :key='index'/>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'ScoreOne',  
    data(){
        return {
            stars: [
                {
                    src: "../../static/img/off.png",
                    active: false
                }, 
                {
                    src: "../../static/img/off.png",
                    active: false
                }, 
                {
                    src: "../../static/img/off.png",
                    active: false
                },
                {
                    src: "../../static/img/off.png",
                    active: false
                }, 
                {
                    src: "../../static/img/off.png",
                    active: false
                }
            ],
            starNum: 0,
        }    
    },
    methods: {
        //评分
        rating: function(index) {
            var total = this.stars.length; //星星总数
            var idx = index + 1; //这代表选的第idx颗星-也代表应该显示的星星数量
            //进入if说明页面为初始状态
            if(this.starNum == 0) {
                this.starNum = idx;
                for(var i = 0; i < idx; i++) {
                    this.stars[i].src = "../../static/img/on.png";
                    this.stars[i].active = true;
                }
            } else {
                //如果再次点击当前选中的星级-仅取消掉当前星级，保留之前的。
                if(idx == this.starNum) {
                    for(var i = index; i < total; i++) {
                        this.stars[i].src = "../../static/img/off.png";
                        this.stars[i].active = false;
                    }
                }
                //如果小于当前最高星级，则直接保留当前星级
                if(idx < this.starNum) {
                    for(var i = idx; i < this.starNum; i++) {
                        this.stars[i].src = "../../static/img/off.png";
                        this.stars[i].active = false;
                    }
                }
                //如果大于当前星级，则直接选到该星级
                if(idx > this.starNum) {
                    for(var i = 0; i < idx; i++) {
                        this.stars[i].src = "../../static/img/on.png";
                        this.stars[i].active = true;
                    }
                }
                var count = 0; //计数器-统计当前有几颗星
                for(var i = 0; i < total; i++) {
                    if(this.stars[i].active) {
                        count++;
                    }
                }
                this.starNum = count;
            }
        },
    }     
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.grade-box img{
    width: 50px;
    height: 50px;
}
.grade-box{
    margin: 20px;
}
</style>