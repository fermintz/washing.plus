<template>
  <div class="home">
    <div class="inner">
      <div class="header">
        <div class="title">
          <h2>
            세탁기플러스
          </h2>
          <p>실시간으로 세탁기의 사용유무를 알 수 있습니다</p>
        </div>
        <div class="langBtns">
          <v-btn outlined v-for="(lang, index) in langs" :key="index" :class="{active:langActive === index}" @click="langActive = index">{{lang}}</v-btn>
        </div>
      </div>

      <div class="noPage">
        <v-icon>mdi-close-circle-outline</v-icon>
        <p>페이지를 찾을 수 없습니다</p>
      </div>

      <div class="customer">
        <dl>
          <dt>문의전화</dt>
          <dd>010-2861-6355</dd>
        </dl>
      </div>
    </div> <!-- inner -->

    <Dialog
      ref="dialog" 
    ></Dialog>
  </div>
</template>

<script>
import Dialog from '@/components/dialog.vue'
// @ is an alias to /src
export default {
  name: "Home",
  components:{
    Dialog,
  },

  data(){
    return{
      activeTab:0,
      tabs:['세탁기','건조기'],
      langActive:0,
      langs:['KOR','ENG'],

      machine:[
        {
          mode:['대기중','사용중','수리중'],
          icon:'@/assets/logo.png',
          name:'1번세탁기',
          time:30,
          overTime:10,
        },
        {
          mode:['대기중','사용중','수리중'],
          icon:'@/assets/logo.png',
          name:'2번세탁기',
          time:30,
          overTime:10,
        }
      ]
    }
  },
}
</script>

<style lang="scss" scoped>

.home{
  background:#262542;
  display:flex;
  justify-content: center;
  align-items:flex-start;
  padding:30px;
  height:100%;

  .inner{
    width:1280px;
  }

  .header{
    display:flex;
    align-items: center;
    justify-content: space-between;
    padding:10px 0;
    color:#fff;

    .title{
      h2{font-size:42px;line-height:42px;font-family:'SCDream'}
      p{color:#aaa;margin-top:5px;font-family:'SCDream'}
    }

    .langBtns{
      .v-btn{
        border:2px solid #fff;
        height:30px;
        margin-left:10px;
        color:#fff;
        border-radius:15px;
        border-color:rgba(255,255,255,0.3);color:rgba(255,255,255,0.3)
      }

      .v-btn.active{border-color:#fff;color:#fff}
    }

  }

  .noPage{
    background:#fff;
    border-radius:5px;
    height:500px;
    box-shadow: 0,0,10px,0.1;

    display:flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    .v-icon{font-size:150px;color:#d2d2d2}
    p{font-size:28px;margin-top:20px;}
  }

  .customer{
    text-align:center;
    background:#000;
    border-radius:5px;
    margin-top:20px;

    dl{
      display:flex;
      justify-content: center;
      align-items: center;
      padding:10px;

      dt{font-size:12px;color:#888}
      dd{color:#fff;margin-left:10px;}
    }
  }
  

}


@media screen and (max-width: 600px) {
  .home{
    padding:20px 0 0px 0;

    .header{
      flex-direction:column;
      justify-content:center;
      align-items: center;

      .title{
        text-align:center;

        h2{line-height:auto}
        p{margin-left:0px;margin-top:10px;font-size:14px;}
      }

      .langBtns{margin-bottom:20px;}
    }

  }
}
</style>