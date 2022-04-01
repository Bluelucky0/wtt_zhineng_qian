<template>
  <div>
    <div class="contence">
      <p class="home"><a href="./main.html">首页</a>><a href="./message.html">游记分享</a>> <span>详情</span></p>
      <div id="travlmess"
           class="travlmess">
        <div class="imgicon"><img src="http://m.tuniucdn.com/fb2/t1/G2/M00/DC/C7/Cii-TFiELNSAAaSQAQ73R312Dmk62_w1536_h0_c0_t0.jpeg"
               alt=""></div>
        <div class="userhead">
          <div class="iconhead">
            <img src="https://img2.baidu.com/it/u=1617362238,740727550&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
                 alt="">
          </div>
          <div class="hedes">
            <p class="username">sil在路上</p>
            <p class="ctime">
              <span>2022-02-03</span>
              <span>206人阅读</span>
            </p>
          </div>
          <div class="cando">
            <div>
              <div class="backgr zan"></div><span>182赞</span>
            </div>
            <div>
              <div class="backgr shoucang"></div><span>122收藏</span>
            </div>
            <div>
              <div class="backgr huifu"></div><span>3回复</span>
            </div>
            <div>
              <div class="backgr fenxiang"></div><span>分享</span>
            </div>
          </div>
        </div>
        <div class="userhead contentcomm">
          <div class="iconhead">
            <img src="https://img2.baidu.com/it/u=1617362238,740727550&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
                 alt="">
          </div>
          <div class="hedes">
            <p class="username">sil在路上</p>
            <p class="ctime">
              <span>发表于 2012-02-03 09：03</span>
            </p>
          </div>
          <div class="cando">1楼</div>
        </div>
        <div class="sharecontence">
          <h2>【序言】</h2>
          <p style="textIndent: 2em;">{{shareData.name}}闻名遐迩的景点,所以我们想要多玩几个地方，便需要安排2-3天才又可能可游玩完。那么，出门旅游-衣食住行，去{{shareData.name}}怎么玩，怎么出行，穿什么衣服，挑什么吃的，又怎么挑住宿的酒店呢？我们一项项分开来说道说道。</p>
          <h2 style="margin:20px 0;fongSize:23px">【 {{shareData.name}}有哪些值得玩？ 】</h2>
          <p style="textIndent: 2em;">{{shareData.introduction}}</p>
          <img :src="shareData.sale"
               alt="">
          <p style="textIndent: 2em;">{{shareData.introduction}}</p>
          <img :src="shareData.sale"
               alt="">
          <p style="textIndent: 2em;">{{shareData.introduction}}</p>
          <img :src="shareData.sale"
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
          <p style="textIndent: 2em;">{{shareData.introduction}}</p>
          <img :src="shareData.sale"
               alt="">
          <p style="textIndent: 2em;">{{shareData.introduction}}</p>
          <img :src="shareData.sale"
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
      shareData: {}
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
    console.log(this.uuid);
    this.$axios.get(`/travel/getTravel/${this.uuid}`).then(res => {
      console.log(res);
      if (res.data) {
        this.shareData = res.data.data
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

.sharecontence h2 {
  margin-top: 30px;
  padding-left: 10px;
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