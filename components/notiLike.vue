<template>
    <div>
        <p class="noteHead">收到的喜欢和赞</p>
        <div class="comment-placeholder">
            <div class="author">
                <div class="avatar" style=""></div>
                <div class="info">
                    <div class="name"></div>
                    <div class="meta"></div>
                </div>
            </div>
            <div class="title"></div>
            <div class="title animated-delay"></div>
            <div class="tool-group">
                <i class="fa fa-thumbs-o-up"></i>
                <div class="zan"></div>
                <i class="fa fa-comment-o"></i>
                <div class="zan"></div>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: 'noti-like'
  }
</script>

<style scoped>
    .noteHead{
        font-size: 16px;
        font-weight: 600;
        margin: 0;
        padding-bottom: 30px;
        border-bottom: 1px solid #eee;
    }
    .avatar {
        width: 38px;
        height: 38px;
        display: inline-block;
        margin-right: 5px;
    }
</style>