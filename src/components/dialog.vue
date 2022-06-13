<template>
  <v-dialog
    width="320px"
    v-model="visible"
  >
    <div class="dialog">
      <div class="cont">
        <p><span>1번세탁기</span>를 수리중으로 변경합니다.</p>
        <v-text-field label="비밀번호" color="#d22828"
        ></v-text-field>
      </div>
      <div class="btns">
        <v-btn text @click="open(false)">완료하기</v-btn>
      </div>
    </div>
  </v-dialog>
</template>

<script>
export default{
  data(){
    return{
      visible:false
    }
  },

  methods:{
    open(value){
      this.visible = value
    }
  }
}
</script>

<style lang="scss" scoped>

.dialog{
  background:#fff;
  padding:15px;
  font-family:'SCDream';
  .cont{
    span{color:#d22828;}
  }

  .btns{
    border-top:1px solid #e2e2e2;
    .v-btn{height:40px;background:#292929;width:100%;color:#fff;}
  }
}

</style>