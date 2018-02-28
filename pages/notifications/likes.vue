<template>
    <div>
        <my-header :headcount="headCount"></my-header>
        <div class="my-container" style="padding:30px 15px">
            <div class="row">
                <div class="col-4">
                    <noti-count :data="notificationCount"></noti-count>
                </div>
                <div class="col-8">
                    <noti-conent></noti-conent>
                </div>
            </div>

        </div>
    </div>

</template>

<script>
  import myHeader from '../../components/myHeader'
  import notiCount from '../../components/notificationsLeft'
  import notiConent from '../../components/notiLike'
  export default {
    name: 'comments',
    components:{
      myHeader,
      notiCount,
      notiConent
    },
    data(){
      return{
        notificationCount:3,
        headCount:2,
      }
    }
  }
</script>

<style scoped>
</style>