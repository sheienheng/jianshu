<template>
    <div class="homepage">
        <my-header></my-header>
        <div class="my-container">
            <div class="row">
                <div class="col-8">
                    <div class="comment-placeholder" style="display: flex;justify-content: space-between">
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
                        <div class="title-right">
                            <a href="javascript:void(0)">
                                <span style="color: #42c02e">发简信</span>
                            </a>
                            <a href="javascript:void(0)" :class=" followchange?'followColor':'followColorchange'"
                               @click="isfollow" @mouseenter="noFollow" @mouseleave="beFollow">
                                <i class="fa fa-plus" ref="faFollow"></i>
                                <span ref="followMes">关注</span>
                            </a>
                        </div>
                    </div>
                    <ul class="homeContent">
                        <li v-for="(actives,index) in actives" @click="conentChange(index)"
                            :class="actives.active">
                            <i :class="faImg[index]"></i><span>{{changeArtic[index]}}</span>
                            <div :class="actives.active"></div>
                        </li>
                    </ul>
                    <div v-for="(com,index2) in components" v-if="actives[index2].active != ''"
                    style="margin-top: 20px">
                        <component v-bind:is="com.com"></component>
                    </div>

                </div>
                <div class="col-4">
                    <Col4></Col4>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
  import myHeader from '../../components/myHeader'
  // import Nuxt from '../../.nuxt/components/nuxt'
  import One from '../../components/users/one'
  import Two from '../../components/users/two'
  import Three from '../../components/users/three'
  import Four from '../../components/users/four'
  import Col4 from '../../components/users/col4'
  export default {
    name: 'myhomepage',
    components:{
      myHeader,
      One,
      Two,
      Three,
      Four,
      Col4
    },
    data(){
      return{
        actives:[
          {active:''},
          {active:'active'},
          {active:''},
          {active:''},
        ],
        faImg:['fa fa-book','fa fa-book','fa fa-book','fa fa-book'],
        changeArtic:['文章','动态','最新评论','热门'],
        components:[{com:'One'},{com:'Two'},{com:'Three'},{com:'Four'}],
        followchange:true,
      }
    },
    methods:{
      isfollow:function(){
        this.followchange=!this.followchange;
        if(this.followchange){
          this.$refs.followMes.innerHTML='关注'
          this.$refs.faFollow.className = 'fa fa-plus';
        }else{
          this.$refs.followMes.innerHTML='已关注'
          this.$refs.faFollow.className = 'fa fa-check';
        }
      },
      noFollow:function(){
        if(!this.followchange){
          this.$refs.followMes.innerHTML='取消关注'
          this.$refs.faFollow.className = 'fa fa-close';
        }
      },
      beFollow:function(){
        if(!this.followchange){
          this.$refs.followMes.innerHTML='已关注'
          this.$refs.faFollow.className = 'fa fa-check';
        }
      },
      conentChange:function(index){
        for(let i in this.actives){
          if(i == index){
            this.actives[i].active='active';
          }else{
            this.actives[i].active='';
          }
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
    .homepage .col-8 .homeContent>li:hover div{
        width: 100%;
        background-color: #333;
    }
    .homepage .col-8 .homeContent>li>div.active{
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
    .homepage .title-right{
        padding-top: 20px;
    }
    .homepage .title-right>a{
        display: inline-block;
        width: 100px;
        text-align: center;
        border: 1px solid #42c02e;
        border-radius: 35px;
        padding: 8px 0;
        margin-left: 20px
    }
    .homepage .title-right a.followColor{
        background-color: #42c02e;
    }
    .homepage .title-right a.followColor i,
    .homepage .title-right a.followColor span{
        color: #fff;
        margin-left: 5px;
    }
    .homepage .title-right a.followColorchange{
        border: 1px solid #c8c8c8;
    }
    .homepage .title-right a.followColorchange i,
    .homepage .title-right a.followColorchange span{
        color: grey;
        margin-left: 5px;
    }
    /*.homepage .col-4 ul li{*/
        /*padding: 10px;*/
        /*font-size: 14px;*/
    /*}*/
    /*.homepage .col-4 ul li i{*/
        /*font-size: 18px;*/
        /*vertical-align: middle;*/
    /*}*/
    /*.homepage .col-4 .addContent{*/
        /*border-bottom: 1px solid #f0f0f0;*/
        /*font-size: 14px;*/
        /*padding: 10px;*/
        /*line-height: 20px;*/
    /*}*/
    /*.homepage .col-4 .addContent span p{*/
        /*margin-bottom: 0;*/
    /*}*/
    /*.homepage .col-4 .addContent span{*/
        /*font-size: 13px;*/
        /*color: #42c02e;*/
    /*}*/
</style>