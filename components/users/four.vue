<template>
    <div id="list-container">
        <ul class="note-list">
            <li class="have-img">
                <nuxt-link class="warp-img" to="/p/_id">
                    <img src="~assets/img/note1.jpg" alt="">
                </nuxt-link>
                <div class="content">
                    <div class="author">
                        <nuxt-link to="/u/123" class="avatar">
                            <img src="~assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                        <div class="info">
                            <nuxt-link to="/u/123" class="nickname">
                                测试用户
                            </nuxt-link>
                            <span class="time">喜欢了文章</span>
                            <span class="time">8小时前</span>
                        </div>
                    </div>
                    <nuxt-link class="title" to="/p/123">
                        如何把书中的只是转化为能力？这是我见过的做好的回答
                    </nuxt-link>
                    <p class="abstract">
                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……
                        不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                    </p>
                    <div class="meta">
                        <nuxt-link to="/p/123" class="colorChange">
                            <i class="fa fa-eye"></i>
                            555
                        </nuxt-link>
                        <nuxt-link to="/p/123" class="colorChange">
                            <i class="fa fa-comment"></i>
                            200
                        </nuxt-link>
                        <span>
                                            <i class="fa fa-heart"></i>
                                            555
                                        </span>
                    </div>
                </div>
            </li>
            <li class="have-img">
                <nuxt-link class="warp-img" to="/p/_id">
                    <img src="~assets/img/note1.jpg" alt="">
                </nuxt-link>
                <div class="content">
                    <div class="author">
                        <nuxt-link to="/u/123" class="avatar">
                            <img src="~assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                        <div class="info">
                            <nuxt-link to="/u/123" class="nickname">
                                测试用户
                            </nuxt-link>
                            <span class="time">喜欢了文章</span>
                            <span class="time">8小时前</span>
                        </div>
                    </div>
                    <nuxt-link class="title" to="/p/123">
                        如何把书中的只是转化为能力？这是我见过的做好的回答
                    </nuxt-link>
                    <p class="abstract">
                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……
                        不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                    </p>
                    <div class="meta">
                        <nuxt-link to="/p/123" class="colorChange">
                            <i class="fa fa-eye"></i>
                            555
                        </nuxt-link>
                        <nuxt-link to="/p/123" class="colorChange">
                            <i class="fa fa-comment"></i>
                            200
                        </nuxt-link>
                        <span>
                                            <i class="fa fa-heart"></i>
                                            555
                                        </span>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: 'four'
  }
</script>

<style scoped>

</style>