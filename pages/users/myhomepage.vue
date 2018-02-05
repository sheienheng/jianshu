<template>
    <div class="homepage">
        <my-header></my-header>
        <div class="my-container">
            <div class="row">
                <div class="col-8">
                    <div class="comment-placeholder">
                        <div class="author">
                            <div class="avatar" style="">
                                <img src="../../assets/img/default-avatar.jpg" alt="">
                            </div>
                            <div class="info">
                                <div class="name">
                                    测试用户
                                </div>
                                <ul class="meta">
                                    <li><p>0</p><a href="javascript:void(0)">关注></a></li>
                                    <li><p>0</p><a href="javascript:void(0)">粉丝></a></li>
                                    <li><p>0</p><a href="javascript:void(0)">文章></a></li>
                                    <li><p>0</p><a href="javascript:void(0)">字数></a></li>
                                    <li><p>0</p><a href="javascript:void(0)">收获喜欢></a></li>
                                </ul>
                            </div>
                        </div>
                    </div>
                    <ul class="homeContent">
                        <li :class="actives[0].active" @click="conentChange(0)"
                            @mouseover="hoverenter(0)" @mouseleave="hoverleave(0)">
                            <i class="fa fa-book"></i><span>文章</span>
                            <div :class="actives[0].active" ref="act0"></div>
                        </li>
                        <li :class="actives[1].active" @click="conentChange(1)"
                            @mouseover="hoverenter(1)" @mouseleave="hoverleave(1)">
                            <i class="fa fa-book"></i><span>动态</span>
                            <div :class="actives[1].active" ref="act1"></div>
                        </li>
                        <li :class="actives[2].active" @click="conentChange(2)"
                            @mouseover="hoverenter(2)" @mouseleave="hoverleave(2)">
                            <i class="fa fa-book"></i><span>最新评论</span>
                            <div :class="actives[2].active" ref="act2"></div>
                        </li>
                        <li :class="actives[3].active" @click="conentChange(3)"
                            @mouseover="hoverenter(3)" @mouseleave="hoverleave(3)">
                            <i class="fa fa-book"></i><span>热门</span>
                            <div :class="actives[3].active" ref="act3"></div>
                        </li>
                    </ul>
                    <div v-if="actives[0].active != ''">
                        111111111111111
                    </div>
                    <div v-if="actives[1].active != ''">
                        222222222222
                    </div>
                    <div v-if="actives[2].active != ''">
                        33333333333
                    </div>
                    <div v-if="actives[3].active != ''">
                        44444444444
                    </div>
                </div>
                <div class="col-4">
                    <ul>
                        <li>
                            <i class="fa fa-heart"></i>
                            我关注的专题/文集/连载
                        </li>
                        <li>
                            <i class="fa fa-heart"></i>
                            我喜欢的文章
                        </li>
                    </ul>
                    <div class="addContent">
                        <p>我创建的专题</p>
                        <span>
                            <i class="fa fa-plus"></i>
                            创建一个新专题
                        </span>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
  import myHeader from '../../components/myHeader'
  export default {
    name: 'myhomepage',
    components:{
      myHeader
    },
    data(){
      return{
        actives:[
          {active:''},
          {active:''},
          {active:'active'},
          {active:''},
        ],

      }
    },
    methods:{
      conentChange:function(index){
        for(let i in this.actives){
          if(i == index){
            this.actives[i].active='active';
          }else{
            this.actives[i].active='';
          }
        }
      },
      hoverenter:function(index){
        if(index == 0){
          this.$refs.act0.classList.add('active2');
        }else if(index == 1){
          this.$refs.act1.classList.add('active2');
        }else if(index == 2){
          this.$refs.act2.classList.add('active2');
        }else if(index == 3){
          this.$refs.act3.classList.add('active2');
        }
      },
      hoverleave:function(index){
        if(index == 0){
          this.$refs.act0.classList.remove('active2');
        }else if( index == 1){
          this.$refs.act1.classList.remove('active2');
        }else if( index == 2){
          this.$refs.act2.classList.remove('active2');
        }else if( index == 3){
          this.$refs.act3.classList.remove('active2');
        }
      }
    }
  }
</script>

<style scoped>
    .homepage .col-8 .avatar {
        width: 80px;
        height: 80px;
        display: inline-block;
        margin-right: 10px;
    }
    .homepage .col-8 .info{
        vertical-align: middle;
    }
    .homepage .col-8 .info .name{
        width: 100%;
        height: 30px;
        font-size: 21px;
        font-weight: 700;
        background-color: #fff;
    }
    .homepage .col-8 .info .meta{
        width: 100%;
        height: 43px;
        display: flex;
        font-size: 12px;
        background-color: #fff;
    }
    .homepage .col-8 .info .meta li{
        padding-right: 7px;
        border-right: 1px solid #f0f0f0;
        margin-right: 7px;
        color: #969696;
    }
    .homepage .col-8 .info .meta li:last-child{
        border-right: none;
    }
    .homepage .col-8 .info .meta li p{
        font-size: 16px;
        margin-bottom: -3px;
        color: #333;
    }
    .homepage .col-8 .homeContent{
        width: 100%;
        display: flex;
        border-bottom: 1px solid #f0f0f0;
    }
    .homepage .col-8 .homeContent>li{
        padding: 13px 0 0 0;
        cursor: pointer;
        color: #969696;
    }
    .homepage .col-8 .homeContent>li.active{
        color: #333;
    }
    .homepage .homeContent>li:hover{
        color: #333;
    }
    .homepage .col-8 .homeContent>li>div{
        width: 0;
        height: 2px;
        margin: 0 auto;
        margin-top: 10px;
        background-color: #fff;
        transition: width .3s linear;
    }
    .homepage .col-8 .homeContent>li>div:hover{
        width: 100%;
        background-color: #333;
    }
    .homepage .col-8 .homeContent>li>div.active,.homepage .homeContent>li>div.active2{
        width: 100%;
        background-color: #333;
    }
    .homepage .col-8 .homeContent>li>i{
        margin-right: 5px;
        padding-left: 20px;
    }
    .homepage .col-8 .homeContent>li>span{
        padding-right: 20px;
    }
    .homepage .col-4 ul{
        margin-top: 40px!important;
        border-top: 1px solid #f0f0f0;
        border-bottom: 1px solid #f0f0f0;
    }
    .homepage .col-4 ul li{
        padding: 10px;
        font-size: 14px;
    }
    .homepage .col-4 ul li>i{
        font-size: 18px;
        vertical-align: middle;
    }
    .homepage .col-4 .addContent{
        border-bottom: 1px solid #f0f0f0;
        font-size: 14px;
        padding: 10px;
        line-height: 20px;
    }
    .homepage .col-4 .addContent span p{
        margin-bottom: 0;
    }
    .homepage .col-4 .addContent span{
        font-size: 13px;
        color: #42c02e;
    }
</style>