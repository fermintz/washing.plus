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

      <div class="tabs">
        <div class="tabHead">
          <v-btn 
            v-for="(tab, index) in tabs" 
            :key="index" 
            :class="{active:activeTab === index}" 
            outlined
            @click="activeTab = index"
          >
            {{tab}}
          </v-btn>
        </div>
        <div class="tabContents" v-show="activeTab == 0">
          <div class="stateBar">
            <dl class="stop">
              <dt>대기중인 장비</dt>
              <dd>05</dd> 
            </dl>
            <dl class="play">
              <dt>작동중인 장비</dt>
              <dd>01</dd> 
            </dl>
            <dl class="repair">
              <dt>수리중인 장비</dt>
              <dd>01</dd>
            </dl>
          </div>

          <div class="guide">
            <b>※</b> 세탁물의 양에 따라 동작시간이 달라질 수 있습니다
          </div>

          <v-row>
            <v-col 
              cols="12"
              xl="4"
              lg="4"
              md="6"
              sm="12"
              xs="12"
              v-for="(item, index) in machine"
              :key="index"
            >
              <div class="item">
                <div class="itemTop">
                  <div class="title use">
                    <span class="use">사용중</span>
                    <label>{{item.name}}</label>
                  </div>
                  <v-btn text @click="$refs.dialog.open(true)">
                    <v-icon>mdi-dots-horizontal</v-icon>
                  </v-btn>
                </div>
                <div class="itemBottom">
                  <div class="icon">
                    <img src="@/assets/img/cool.gif">
                  </div>
                  <div class="time">
                    <dl>
                      <dt>남은시간</dt>
                      <dd>
                        <strong>30</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                  <div class="time">
                    <dl>
                      <dt>초과동작</dt>
                      <dd>
                        <strong>0</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                </div> <!-- itemBottom -->
              </div> <!-- item -->
            </v-col>

            <v-col 
              cols="12"
              xl="4"
              lg="4"
              md="6"
              sm="12"
              xs="12"
              v-for="(item, index) in machine"
              :key="index"
            >
              <div class="item">
                <div class="itemTop">
                  <div class="title use">
                    <span class="stop">대기중</span>
                    <label>{{item.name}}</label>
                  </div>
                  <v-btn text @click="$refs.dialog.open(true)">
                    <v-icon>mdi-dots-horizontal</v-icon>
                  </v-btn>
                </div>
                <div class="itemBottom">
                  <div class="icon">
                    <img src="@/assets/img/stop.png">
                  </div>
                  <div class="time">
                    <dl>
                      <dt>남은시간</dt>
                      <dd>
                        <strong>30</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                  <div class="time">
                    <dl>
                      <dt>초과동작</dt>
                      <dd>
                        <strong>0</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                </div> <!-- itemBottom -->
              </div> <!-- item -->
            </v-col>
          </v-row>
        </div>
        <div class="tabContents"  v-show="activeTab == 1">

          <div class="stateBar">
            <dl class="stop">
              <dt>대기중인 장비</dt>
              <dd>05</dd> 
            </dl>
            <dl class="play">
              <dt>작동중인 장비</dt>
              <dd>01</dd> 
            </dl>
            <dl class="repair">
              <dt>수리중인 장비</dt>
              <dd>01</dd>
            </dl>
          </div>

          <div class="guide">
            <b>※</b> 세탁물의 양에 따라 동작시간이 달라질 수 있습니다
          </div>

          <v-row>
            <v-col 
              cols="12"
              xl="4"
              lg="4"
              md="6"
              sm="12"
              xs="12"
              v-for="item in 5"
              :key="item"
            >
              <div class="item">
                <div class="itemTop">
                  <div class="title stop">
                    <span class="use">사용중</span>
                    <label>{{item}}번 건조기</label>
                  </div>
                  <v-btn text>
                    <v-icon>mdi-dots-horizontal</v-icon>
                  </v-btn>
                </div>
                <div class="itemBottom">
                  <div class="icon">
                    <img src="@/assets/img/hot.gif">
                  </div>
                  <div class="time">
                    <dl>
                      <dt>남은시간</dt>
                      <dd>
                        <strong>30</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                  <div class="time">
                    <dl>
                      <dt>초과동작</dt>
                      <dd>
                        <strong>0</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                </div> <!-- itemBottom -->
              </div> <!-- item -->
            </v-col>
            <v-col 
              cols="12"
              xl="4"
              lg="4"
              md="6"
              sm="12"
              xs="12"
            >
              <div class="item">
                <div class="itemTop">
                  <div class="title">
                    <span class="repair">수리중</span>
                    <label>6번 건조기</label>
                  </div>
                  <v-btn text>
                    <v-icon>mdi-dots-horizontal</v-icon>
                  </v-btn>
                </div>
                <div class="itemBottom">
                  <div class="icon">
                    <img src="@/assets/img/repair.png">
                  </div>
                  <div class="time">
                    <dl>
                      <dt>남은시간</dt>
                      <dd>
                        <strong>30</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                  <div class="time">
                    <dl>
                      <dt>초과동작</dt>
                      <dd>
                        <strong>0</strong>
                        <span>분</span>
                      </dd>
                    </dl>
                  </div>
                </div> <!-- itemBottom -->
              </div> <!-- item -->
            </v-col>
          </v-row>
        </div> <!-- tabContents -->
      </div> <!-- tabs -->
     
      <div class="footer">
        <v-row>
          <v-col cols="12" xl="8" lg="8" md="8" sm="12" xs="12">
            <div class="banner">
              <img src="@/assets/img/poinplus.png">
              <dl>
                <dt>세탁기 간편결제앱 포인플러스</dt>
                <dd>지금 바로 설치해보세요</dd>
              </dl>
            </div>
          </v-col>
          <v-col cols="12"  xl="4" lg="4" md="4" sm="12" xs="12">
             <div class="btns">
              <v-btn text width="50%" height="100%">
                <div class="bannerBtn">
                  <img src="@/assets/img/play.png">
                  <span>Play Store</span>
                </div>
              </v-btn>
              <v-btn text width="50%" height="100%">
                <div class="bannerBtn">
                  <img src="@/assets/img/app.png">
                  <span>App Store</span>
                </div>
              </v-btn>
            </div>
          </v-col>
        </v-row>
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


  

  .tabs{
     border-radius:5px;
     overflow:hidden;
     box-shadow: 0 0 30px rgba(0,0,0,0.1);

    .tabHead{
      height:60px;background:#343358;

      .v-btn{height:60px;width:50%;border:0px;border-radius:0px;color:#fff;font-size:18px}
      .v-btn.active{background:#fff;border-radius:5px 5px 0 0;color:#2816A7;}
    }

    .tabContents{
      padding:30px;
      background:#fff;
      min-height:720px;

      .stateBar{
        background:#fff;
        color:#292929;
        display:flex;
        align-items: center;
        padding:15px 10px;
        border-radius: 5px;
        margin-bottom:20px;
        box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        border:1px solid #e2e2e2;

        display:flex;

        dl{
          flex:1;
          border-right:1px solid #e2e2e2;
          margin:0 10px;

          dt{font-size:14px;color:#888}
          dd{font-size:20px;font-weight:600}
        }
        dl:last-child{border-right:0px;}

        dl.stop{
          dd{color:#292929}
        }

        dl.play{
          dd{color:#2816A7}
        }

        dl.repair{
          dd{color:#00919D}
        }
      }
    }

    .guide{
      margin:30px 0 20px 0;text-align:center;
      background:#FFF3F3;padding:5px 15px;border-radius:5px;

      b{color:#d22828;font-weight:normal}
    }
  }

  .item{
    display:flex;
    flex-direction: column;
    background:#fff;
    border-radius:5px;
    border:1px solid #e2e2e2;
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);

    .itemTop{
      border-bottom:1px solid #e2e2e2;;
      display:flex;
      justify-content:space-between;
      align-items: center;
      height:50px;
      padding:0 5px 0 15px;
      background:#f8f8f8;

      .title{
        display:flex;
        align-items: center;

        span{font-family:'SCDream';font-size:12px;color:#fff;;display:inline-block;height:24px;border-radius:12px;padding:0 10px;line-height:24px;}
        label{font-family:'SCDream';font-size:18px;margin-left:10px;}
      }

      span.use{background:#2816A7}
      span.stop{background:#292929}
      span.repair{background:#00919D}

      .v-btn{width:30px;height:30px;}
    }

    .itemBottom{
      flex:1;
      display:flex; 
      justify-content: space-around;
      align-items: center;
      text-align:center;
      padding:15px 0;

      img{width:auto;height:100%;}

      .time{
        dt{font-size:14px;}
        dd{
          strong{font-size:32px;font-weight:600}
          span{margin-left:3px;}
        }
      }
    }

    .itemBottom > div{
      flex:1;
      display:flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height:100%;
      border-right:1px solid #e2e2e2;
      height:100px;
    }
    .itemBottom > div:last-child{border-right:0px;}
  }

  .footer{
    margin-top:20px;
    border-radius:5px;
    display:flex;
    justify-content: space-between;
    align-items: center;
    position:relative;

    .banner{
      position:relative;
      background:#E2EAEF;
      border-radius:5px;
      display:flex;
      align-items: center;
      justify-content: flex-end;
      height:120px;

      img{
        position:absolute;
        left:30px;
        bottom:0px;
      }

      dl{
        text-align:right;
        margin-right:30px;
        dt{font-size:16px;color:#494949;}
        dd{font-size:28px;font-weight:600;color:#2816A7}
      }
    }

    .btns{
      display:flex;
      width:100%;
      background:#fff;
      height:120px;
      border-radius:5px;

      .v-btn:last-child{background:#f2f2f2;}

      span{display:block; font-size:12px;margin-top:5px;}
    }
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

    .tabs{
      border-radius:0px;
      .tabContents{padding:30px 15px;}
    }

    .guide{
      text-align:center;
    }

    .footer{

      .banner{
        border-radius:0px;
        border:0px;

        dl{
          dt{font-size:14px;}
          dd{font-size:24px;}
        }
      }

      .btns{border-radius:0px;margin-top:-24px;}
    }
  }

  
}

</style>