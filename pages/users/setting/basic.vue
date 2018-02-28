<template>
    <div>
        <my-header></my-header>
        <div class="my-container" style="padding:30px 15px">
            <div class="row">
                <div class="col-4">
                    <sett-count :data="settingCount"></sett-count>
                </div>
                <div class="col-8">
                    <setting-conent></setting-conent>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
  import myHeader from '../../../components/myHeader'
  import settCount from '../../../components/settingLeft'
  import settingConent from '../../../components/settbasic'
  export default {
    name: 'basic',
    components:{
      myHeader,
      settCount,
      settingConent
    },
    data(){
      return{
        settingCount:0,
      }
    }
  }
</script>

<style scoped>
</style>