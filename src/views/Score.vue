<template>
  <div>
    <div class="your_scores_container">
      <header class="your_scores">
        <span class="score_num">{{score}}</span>
        <span class="fenshu">分！</span>
      </header>
      <div class="result_tip">{{scoreTips}}</div>
    </div>
    <div class="share_button" @click="showCover"></div>
    <div class="share_cover" v-show="showHide" @click="showCover">
      <img src="../assets/5-2.png" alt="" class="share_img">
    </div>
  </div>
</template>

<script>
import {mapState} from 'vuex'
// @ is an alias to /src


export default {
  name: 'score',
  data() {
    return {
      showHide: false,
      score: 0,
      scoreTips: '',
      rightAnswer: [2, 7, 12, 13, 18],
      scoreTipeArr: ['你说，是不是把知识都还给小学老师了？', '还不错，但还需要继续加油哦！', '不要嘚瑟还有进步的空间！', '智商离爆表只差一步了！', '你也太聪明啦，葡萄之家欢迎你！']
    }
  },
  computed: mapState(['answerid']),
  created() {
    this.computedScore()
    this.getScoreTip()
    document.body.style.backgroundImage = 'url(./img/4-1.4c4bb05d.jpg)'
  },
  methods: {
    computedScore() {
      this.answerid.forEach((item,index)=>{
          if(item == this.rightAnswer[index]) {
          this.score += 20
        }
      })
    },
    showCover() {
     this.showHide = !this.showHide
    },
    getScoreTip() {
      let index = Math.ceil(this.score/20) - 1
      this.scoreTips = this.scoreTipeArr[index]
    }
  }
}
</script>
<style lang="less">
body {
  background-image: url(../assets/4-1.jpg);
  padding-top: 1.2rem;
}
.your_scores_container{
  width: 9.7rem;
  height: 9.1rem;
  background: url(../assets/4-2.png) no-repeat;
  background-size: 100% 100%;
  margin: 0 auto 0;
  position: relative;
  .your_scores{
      position: absolute;
      width: 100%;
      text-indent: 3.3rem;
      top: 4.7rem;
      font-size: 1.4rem;
      font-weight: 900;
      -webkit-text-stroke: 0.05rem #412318;
      font-family: 'Microsoft YaHei';
      .score_num{
          font-family: Tahoma,Helvetica,Arial;
          color: #a51d31;
      }
      .fenshu{
          color: #a51d31;
      }
  }
  .result_tip{
      position: absolute;
      top: 7rem;
      width: 9rem;
      left: 0.6rem;
      color: #3e2415;
      font-size: 0.65rem;
      text-align: center;
  }
}
.share_button{
  width: 6.025rem;
  height: 2.4rem;
  margin: 0.8rem auto 0;
  background: url(../assets/4-3.png) no-repeat 0.4rem 0;
  background-size: 5.825rem 100%;
}
.share_cover{
  position: fixed;
  bottom: 0;
  right: 0;
  top: 0;
  left: 0;
  background: url(../assets/5-1.png) no-repeat;
  background-size: 100% 100%;
  opacity: 0.92;
}
.share_img{
  height: 10.975rem;
  width: 11.95rem;
  position: fixed;
  top: 0.5rem;
  left: 50%;
  margin-left: -5.975rem;
}
</style>