<template>
  <section class="error">
    <div class="error-log">
    <img src="~assets/img/jianshu.com.png" alt="">
    </div>
    <div class="error-404">
      <img src="~assets/img/404.jpg" alt="">
      <h3>您要找的页面不存在</h3>
      <div class="sub-title">可能是因为您的链接地址有误、该文章已经被作者删除或转为私密状态。</div>
      <div class="btn">返回「简书」首页</div>
    </div>
    <nuxt-link class="button" to="/" v-if="error.statusCode === 404">
    </nuxt-link>
  </section>
</template>
<script>
  export default{
    props: ['error'],
    head () {
      return{
        title:"您找的页面不存在",
        meta:[
          {hid: 'description',name:'description',content:'您找的页面不存在'}
        ]
      }
    }
  }

</script>
<style>
.error{
    text-align: center;
  }
.error-log{
  position: absolute;
  top: 50px;
  left: 0;
}
.error-log img{
  width: 60%;
}
.error-404{
    text-align: center;
}
.error-404 img{
  width: 220px;
  margin-top: 100px;
  }
.error-404 h3{
    font-size: 1.17em;
    font-weight: bold;
    margin: 40px 0 20px 0;
  }
.error-404 .sub-title{
  margin: 10px 0 30px 0;
  font-size: 14px;
}
.error-404 .btn{
        padding: 13px 0;
        width: 160px;
        font-size: 15px;
        display: inline-block;
        background-color: #42C02E;
        color: #fff;
        border-radius: 40px;
    }
@media (max-width:1050px) {
  .error-log{
    display: none;
  }
}
</style>
