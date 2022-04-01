<template>
  <div>
    <div class="contence">
      <p class="home"><a href="#/header/main">首页</a>><span>游记攻略</span></p>
      <div class="online_search">
        <div class="selectjob">攻略</div>
        <input type="text"
               class="search_word"
               id="keyword"
               placeholder="请输入您的关键词"
               autocomplete="off">
        <div class="tosee"
             onclick="searchCourse()">
          <img src="../assets/image/search_rgba.png"
               alt="">
          <div>搜索</div>
        </div>
      </div>
      <div id="travlmess"
           class="travlmess">
        <div class="rankingmessage">
          <div class="module_title">您感兴趣的攻略</div>
          <div class="rankings"
               id="rankings">
            <a href=""
               target="_self"
               v-for="(item,index) in datas"
               :key="item.uuid">
              <span class="title">4天{{item.name}}自由行，坐动车下午2点多到{{item.name}}，求各位大神指导攻略，谢谢！</span>
            </a>
          </div>
        </div>
        <div class="messages">
          <ul class="messageEach">
            <li v-for="(item,index) in datas"
                :key="item.uuid">
              <div class="text_mess">
                <p class="title_content">只有1天时间，怎样才能玩出{{item.name}}的精华？</p>
                <p class="messscontent">{{item.introduction}}</p>
                <p class="createtime">
                  <span>2022-01-11</span>
                  <span class="like">
                    <img src="../assets/image/gray_like.png"
                         alt="">
                    <span>{{item.hot}}</span>
                  </span>
                </p>
              </div>
              <img :src="item.sale">
            </li>
          </ul>
        </div>
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
      datas: []
    }
  },
  methods: {
    changelb () {
      this.loginbool = !this.loginbool
    }
  },
  mounted () {
    this.$axios.get('/travel/randomTravel').then(res => {
      if (res.data) {
        this.datas = res.data.data
        this.reload()
      }
    })
  },
}
</script>

<style scoped>
.header {
  position: static !important;
  background: rgba(45, 51, 54, 0.9);
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

.online_search {
  position: relative;
  display: flex;
  align-items: center;
  width: 1200px;
  height: 80px;
  line-height: 80px;
  background: rgba(255, 255, 255, 1);
  box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
  border-radius: 4px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  margin: 25px auto 0 auto;
}

.selectjob {
  width: 160px;
  height: 60px;
  line-height: 60px;
  text-align: center;
  box-sizing: border-box;
  border: none;
  border-right: 1px solid rgba(206, 206, 206, 1);
  font-size: 20px;
  color: rgba(52, 52, 52, 1);
}

.search_word {
  width: 897px;
  font-size: 18px;
  box-sizing: border-box;
  padding-left: 20px;
  color: rgba(52, 52, 52, 1);
}

.search_word::placeholder {
  color: rgba(151, 151, 151, 1);
}

.tosee {
  position: absolute;
  right: 0;
  top: 0;
  display: flex;
  align-items: center;
  width: 160px;
  height: 80px;
  background: rgba(17, 123, 241, 1);
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.15);
  border-radius: 0 4px 4px 0;
  font-size: 20px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(255, 255, 255, 1);
}

.tosee img {
  width: 19px;
  height: 20px;
  padding-left: 45px;
  padding-right: 10px;
}

.travlmess {
  display: flex;
  justify-content: space-between;
  margin-top: 43px;
}

.rankingmessage {
  width: 30%;
  background: #fff;
}

.module_title {
  font-size: 45px;
  height: 120px;
  line-height: 120px;
  text-align: center;
  font-weight: bold;
  background: #0b7cd2;
  color: #ffffff;
}

.rankings {
  width: 100%;
  box-sizing: border-box;
  padding: 30px 0 30px 20px;
}
.rankings .title {
  /* 文字开头空格 */
  text-indent: 2em;
  font-size: 26px;
  line-height: 42px;
  text-overflow: ellipsis;
  word-break: break-all;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
}
.rankings .title:hover {
  color: #ff9d00;
}
.rankings > a {
  padding: 20px;
  width: 100%;
  box-sizing: border-box;
  overflow: hidden;
  vertical-align: top;
  text-align: left;
  border: 1px solid #e7e7e7;
  color: #4c4c4c;
  font-size: 30px;
  margin-top: 30px;
}

.rankings > a:hover {
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.2);
}

.rankings > a:first-child {
  margin-top: 0;
}

.messages {
  width: 67%;
}

.messageEach {
  width: 100%;
  padding: 30px;
  box-sizing: border-box;
  background: #fff;
}

.messageEach li {
  width: 100%;
  height: 190px;
  box-sizing: border-box;
  padding: 15px 20px;
  border-bottom: 1px dashed rgb(243, 243, 243);
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  border: 1px solid #e7e7e7;
  white-space: nowrap;
  margin-top: 40px;
}

.messageEach li:hover {
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.2);
}

.messageEach li:first-child {
  margin-top: 0;
}

.text_mess {
  width: 81%;
  font-size: 22px;
  font-family: PingFangSC-Medium, PingFang SC;
  font-weight: 500;
  color: rgba(52, 52, 52, 1);
  letter-spacing: 1px;
}

p.title_content {
  font-size: 25px;
  font-weight: 600;
  color: rgba(52, 52, 52, 1);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

p.messscontent {
  padding-top: 10px;
  text-indent: 2em;
  white-space: pre-wrap;
  text-align: justify;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}

.createtime {
  display: flex;
  padding-top: 20px;
  align-items: center;
  justify-content: space-between;
}

.title_content:hover {
  color: #ff9d00;
}

span.like {
  display: flex;
  align-items: center;
}

span.like img {
  width: 30px;
  padding-right: 10px;
}

.messageEach li > img {
  width: 150px;
  height: 130px;
  border-radius: 4px;
}
</style>