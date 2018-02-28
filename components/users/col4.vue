<template>
    <div>

        <div class="compile">
            <div class="title">
                <span>个人介绍</span>
                <a href="javascript:void(0)" @click="compileShow=true"><i class="fa fa-pencil"></i> 编辑</a>
            </div>
            <div v-if="compileShow" style="padding-top: 25px">
                <textarea></textarea>
                <input type="submit" value="保存" class="btn btn-hollow">
                <a href="javascript:void(0)" @click="compileShow=false">取消</a>
            </div>
        </div>
        <ul>
            <li>
                <nuxt-link :to="{path:'/users/likeBook',query:{num:0}}">
                <i class="fa fa-th-large"></i>
                我关注的专题/文集/连载
                </nuxt-link>
            </li>
            <li>
                <nuxt-link :to="{path:'/users/likeBook',query:{num:1}}">
                <i class="fa fa-heart-o"></i>
                我喜欢的文章
                </nuxt-link>
            </li>
        </ul>
        <div class="addContent">
            <p>我创建的专题</p>
            <nuxt-link to="/users/new">
                <span>
                    <i class="fa fa-plus"></i>
                    创建一个新专题
                </span>

            </nuxt-link>
        </div>
    </div>
</template>

<script>
  export default {
    name: 'col4',
    data(){
      return{
        compileShow:false
      }
    }
  }
</script>

<style scoped>
    .compile{
        padding-top: 25px;
        margin-bottom: 25px;
    }
    .compile .title{
        display: flex;
        justify-content: space-between;
        /*padding-bottom: 25px;*/
        font-size: 14px;
        color: #969696;
    }
    .compile .title a:hover{
        color: #333!important;
    }
    .compile div textarea{
        width: 100%;
        height: 120px;
        resize : none;
        margin-bottom: 20px;
    }
    .compile div input.btn-hollow{
        margin-right: 20px;
        background-color: #fff;
        border-radius: 15px;
        padding: 5px 20px;
        font-size: 14px;
        border:1px solid #42c02e;
        color: #42c02e!important;
    }
    ul{
        /*margin-top: 40px!important;*/
        border-top: 1px solid #f0f0f0;
        border-bottom: 1px solid #f0f0f0;
    }
    ul li{
        padding: 10px;
        font-size: 14px;
    }
    ul li i{
        font-size: 18px;
        vertical-align: middle;
    }
    .addContent{
        border-bottom: 1px solid #f0f0f0;
        font-size: 14px;
        padding: 10px;
        line-height: 20px;
    }
    .addContent p{
        margin-bottom: 10px;
    }
    .addContent a{
        font-size: 13px;
        color: #42c02e!important;
    }
</style>