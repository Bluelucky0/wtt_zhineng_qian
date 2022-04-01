<template>
  <div>
    <div class="contence">
      <p class="home"><a href="./main.html">首页</a>><a href="./message.html">游记攻略</a>> <span>详情</span></p>
      <div id="travlmess"
           class="travlmess">
        <div class="sharecontence">
          <h1>{{strategyData.name}}超实用攻略，找个周末去爬山赏水喝茶</h1>
          <div class="right">
            <span>游记攻略</span>
            <span>2022.03.10</span>
            <span>阅读 {{strategyData.hot}}</span>
          </div>
          <p style="textIndent: 2em;">{{strategyData.name}}闻名遐迩的景点,所以我们想要多玩几个地方，便需要安排2-3天才又可能可游玩完。那么，出门旅游-衣食住行，去{{strategyData.name}}怎么玩，怎么出行，穿什么衣服，挑什么吃的，又怎么挑住宿的酒店呢？我们一项项分开来说道说道。</p>
          <h2 style="margin:20px 0;fongSize:23px">【 {{strategyData.name}}有哪些值得玩？ 】</h2>
          <p style="textIndent: 2em;">{{strategyData.introduction}}</p>
          <img :src="strategyData.sale"
               alt="">
          <p style="textIndent: 2em;">{{strategyData.introduction}}</p>
          <img :src="strategyData.sale"
               alt="">
          <p style="textIndent: 2em;">{{strategyData.introduction}}</p>
          <img :src="strategyData.sale"
               alt="">
          <div class="bottomconece">
            <span>最后编辑于： 2022-02-03 20:13</span>
            <span class="reply"><img src="../assets/image/mineorderdpj.png"
                   alt=""> <span>回复</span></span>
          </div>
        </div>
        <div class="userhead contentcomm">
          <div class="iconhead">
            <img src="https://img2.baidu.com/it/u=3804069081,3968854353&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
                 alt="">
          </div>
          <div class="hedes">
            <p class="username">层析小寒</p>
            <p class="ctime">
              <span>发表于 2022-02-28 12：23</span>
            </p>
          </div>
          <div class="cando">2楼</div>
        </div>
        <div class="sharecontence">
          <h2>【我来补充一些】</h2>
          <p style="textIndent: 2em;">{{strategyData.introduction}}</p>
          <img :src="strategyData.sale"
               alt="">
          <p style="textIndent: 2em;">{{strategyData.introduction}}</p>
          <img :src="strategyData.sale"
               alt="">
          <div class="bottomconece">
            <span></span>
            <span class="reply"><img src="../assets/image/mineorderdpj.png"
                   alt=""> <span>回复</span></span>
          </div>
        </div>
      </div>
      <div class="replaythos">
        <div class="iconhead">
          <img src="../assets/image/usericon.png"
               alt="">
        </div>
        <textarea name=""
                  id=""
                  class="replycontnce"
                  placeholder="回复当前游记分享"></textarea>
      </div>
    </div>
    <footers></footers>
    <evelator></evelator>
    <login v-show="loginbool"
           @closelogin="changelb"></login>
  </div>
</template>

<script>
export default {
  name: '',
  data () {
    return {
      loginbool: false,
      uuid: '',
      strategyData: {}
    }
  },
  methods: {
    changelb () {
      this.loginbool = !this.loginbool
    },
  },
  mounted () {
    // 推荐详情
    this.uuid = this.$route.query.uuid
    this.$axios.get(`/travel/getTravel/${this.uuid}`).then(res => {
      console.log(res);
      if (res.data) {
        this.strategyData = res.data.data
      }
    })
  },
}
</script>

<style scoped>
body,
html {
  background: rgb(255, 255, 255) !important;
}
.contence {
  width: 1520px;
  margin: 0 auto;
  position: relative;
}

.home {
  padding-top: 25px;
  padding-bottom: 20px;
  font-size: 25px;
  font-family: PingFangSC-Medium, PingFang SC;
  font-weight: 500;
  color: rgba(52, 52, 52, 1);
  border-bottom: 3px solid rgba(17, 123, 241, 1);
}

.home a {
  color: rgba(52, 52, 52, 1);
}

.home a:hover {
  color: rgba(17, 123, 241, 1);
}

.home span {
  color: rgba(17, 123, 241, 1);
}

div#travlmess {
  width: 100%;
  margin-top: 30px;
  font-family: PingFangSC-Medium, PingFang SC;
}

.imgicon {
  width: 100%;
  height: 420px;
}

.imgicon > img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.userhead {
  background: #f1f1f1;
  height: 130px;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
  padding: 0 100px 0 280px;
}

.iconhead {
  position: absolute;
  top: -78%;
  left: 40px;
  width: 180px;
  height: 180px;
  border: 10px solid #f0f0f0;
  border-radius: 50%;
}

.iconhead > img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
}

p.username {
  font-size: 34px;
}

p.ctime {
  font-size: 25px;
  color: #636363;
  padding-top: 20px;
  padding-left: 30px;
}

.ctime > span:last-child {
  padding-left: 30px;
}

.cando {
  cursor: pointer;
  display: flex;
}

.cando > div {
  width: 150px;
  height: 100px;
  text-align: center;
  color: #636363;
  border-right: 1px solid #e9e9e9;
}

.backgr {
  width: 40px;
  height: 40px;
  margin: 0 auto;
}

.zan {
  background: url(../assets/image/nosupport.png) no-repeat;
  background-size: 100% 100%;
}

.shoucang {
  background: url(../assets/image/nocollect.png) no-repeat;
  background-size: 100% 100%;
}

.huifu {
  background: url(../assets/image/mineorderdpj.png) no-repeat;
  background-size: 100% 100%;
}

.fenxiang {
  background: url(../assets/image/share.png) no-repeat;
  background-size: 100% 100%;
}

.cando > div > span {
  font-size: 25px;
  padding-top: 17px;
}

.userhead.contentcomm {
  margin-top: 50px;
  height: 80px;
  border-radius: 10px;
  padding: 0 60px 0 180px;
  background: #f1f1f1;
}

.userhead.contentcomm .iconhead {
  width: 90px;
  height: 90px;
  top: -50%;
  border-color: #fff;
}

.contentcomm .username {
  font-size: 27px;
}

.contentcomm .ctime {
  font-size: 20px;
  padding-top: 8px;
  padding-left: 10px;
}

.contentcomm .cando {
  font-size: 30px;
  color: #424242;
}

.sharecontence {
  padding: 0 0 100px 0;
}

.sharecontence h1 {
  margin: 30px 0;
  color: #ff7800;
}
.sharecontence .right {
  float: right;
}
.sharecontence .right span {
  color: #959595;
  margin: 0 15px;
}
.sharecontence p {
  font-size: 30px;
  padding-top: 40px;
  line-height: 50px;
}

.sharecontence img {
  width: 80%;
  height: 800px;
  display: block;
  margin: 40px auto 20px auto;
}

.bottomconece {
  margin-top: 100px;
  height: 50px;
  font-size: 20px;
  color: #959595;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.bottomconece img {
  width: 30px;
  height: 30px;
  padding-right: 20px;
  margin: 0;
}

.reply {
  display: flex;
  align-items: center;
  font-size: 25px;
  color: #2cdbb0;
}

.replaythos {
  position: relative;
  display: flex;
}

.replaythos .iconhead {
  width: 90px;
  height: 90px;
  top: -50%;
  border-color: #fff;
  position: static;
}

textarea.replycontnce {
  margin-left: 30px;
  width: 91%;
  height: 200px;
  border: 1px solid #d7d7d7;
  border-radius: 4px;
  padding: 15px;
  box-sizing: border-box;
}

.replycontnce::placeholder {
  color: silver;
}
</style>