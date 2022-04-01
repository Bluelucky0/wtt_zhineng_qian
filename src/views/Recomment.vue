<template>
  <div>
    <div class="contence">
      <p class="home"><a href="#/header/main">首页</a>><span>景区</span></p>
      <div class="online_search">
        <div class="selectjob">景区</div>
        <input type="text"
               class="search_word"
               ref="seakey"
               v-model="tag"
               placeholder="请输入您期望景区的关键词"
               autocomplete="off"
               @keypress="keysearch">
        <div class="tosee"
             @click="searchCourse()">
          <img src="../assets/image/search_rgba.png"
               alt="">
          <div>搜索</div>
        </div>
      </div>
      <div class="history_search">
        <div class="history_title">历史搜索：</div>
        <ul class="search_his">
          <li>武夷旅游</li>
        </ul>
      </div>
      <div class="allcourses">
        <div class="recomment">
          <div class="row row-feature mfw-acc-hide row-bg">
            <div class="recomcourse">
              <span class="coursetitle"> 热门推荐</span>
            </div>
            <div class="wrapper">
              <!-- 热门推荐 -->
              <el-row :gutter="20">
                <el-col :span="8"
                        v-for="(item,index) in hotData"
                        :key="item.uuid">
                  <el-card shadow="hover">
                    <div class="two"
                         @click="toHotel">
                      <span class="no">1</span>{{item.name}}
                      <div class="photo">
                        <img :src="item.sale"
                             width="100%"
                             height="156px">
                      </div>
                      <div class="text">
                        {{item.introduction}}
                      </div>
                    </div>
                  </el-card>
                </el-col>
              </el-row>
              <!-- 分页器 -->
              <el-pagination small
                             background=true
                             layout="prev, pager, next"
                             :total="50">
              </el-pagination>
            </div>
          </div>
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
      tag: '',
      label: '',
      hotData: [],
      params: {}
    }
  },
  methods: {
    toDetail () {
      this.$router.push('/header/recoment')
      window.scrollTo(0, 0)
    },
    toSpot () {
      this.$router.push('/header/recomdetails')
    },
    changelb () {
      console.log(this)
      this.loginbool = !this.loginbool
    },
    // 搜索
    searchCourse (key) {
      let keyparam = {}
      if (key) {
        keyparam.tag = key
      } else {
        keyparam.tag = this.tag
      }
      if (keyparam.tag) {
        this.$axios.post('/travel/globalSearch', keyparam).then(res => {
          if (res.data) {
            this.hotData = res.data.data
          }
        })
      } else {
        layer.msg("请输入您想要搜索的内容")
      }
    },
    keysearch (e) {
      var keycode = e.keyCode;
      if (keycode == '13') {
        e.preventDefault();
        this.searchCourse()
      }
    },
  },
  mounted () {
    this.params.label = this.$route.query.label
    if (this.params.label == undefined) {
      // 调随机景区接口
      this.$axios.get('/travel/randomTravel').then(res => {
        // console.log(res);
        if (res.data) {
          this.hotData = res.data.data
        }
      })
    } else {
      this.$axios.post('/travel/getTravelByLabel', this.params).then(res => {
        console.log(res);
        if (res.data) {
          this.hotData = res.data.data
        }
      })
    }
    if (this.$route.params.befocus) {
      this.$refs.seakey.focus()
    }
    // 顶部导航跳转搜索
    if (this.$route.query.gosearch) {
      let Tag = {}
      Tag.tag = this.$route.query.gosearch
      this.$axios.post('/travel/globalSearch', Tag).then(res => {
        if (res.data) {
          this.hotData = res.data.data
          this.reload()
        }
      })
    }
  }
}
</script>

<style scoped>
.wrapper .text {
  margin: 15px 0;
  width: 100%;
  height: 60px;
  /* 文字开头空格 */
  text-indent: 2em;
  font-size: 15px;
  line-height: 20px;
  text-overflow: ellipsis;
  word-break: break-all;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
}
.allcourses {
  width: 1520px;
  margin: 0 auto;
}
.recomment {
  margin-top: 46px;
}
.recomcourse {
  padding: 14px 0 14px 20px;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 4px solid rgba(17, 123, 241, 1);
}
.wrapper {
  margin-top: 25px;
}
.el-pagination {
  height: 40px;
  text-align: center;
}
.row-bg {
  background-color: #fafafa;
}
.row {
  padding: 40px 0;
  min-width: 980px;
  border-bottom: 1px solid #e4e4e4;
}
.el-row {
  margin-bottom: 20px;
}
.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
  margin-bottom: 15px;
}
.grid-content > h2 {
  text-align: center;
  margin-top: 20px;
}
.grid-content > h2:hover {
  color: rgb(233, 160, 25);
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
.no {
  float: left;
  margin: 4px 10px 0 0;
  width: 25px;
  height: 25px;
  background-color: #ff9d00;
  border-radius: 3px;
  text-align: center;
  color: #fff;
  font-size: 16px;
  line-height: 20px;
}
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
  padding-bottom: 25px;
  font-size: 20px;
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
  cursor: pointer;
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
.history_search {
  padding-top: 20px;
  font-size: 14px;
  display: flex;
  align-items: center;
}
.history_title {
  font-family: PingFangSC-Medium, PingFang SC;
  font-weight: 500;
  color: rgba(151, 151, 151, 1);
}
.search_his {
  display: flex;
  flex-wrap: nowrap;
}
.search_his li {
  padding-left: 20px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(17, 123, 241, 1);
  cursor: pointer;
}
.classify {
  transition: all 0.3s;
  padding: 30px 0 15px 0;
  font-size: 16px;
  display: flex;
  align-items: center;
  border-bottom: 1px solid rgba(216, 216, 216, 1);
}
.kindsclass {
  font-family: PingFangSC-Medium, PingFang SC;
  font-weight: 500;
  color: rgba(52, 52, 52, 1);
}
.kindsclass span {
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(17, 123, 241, 1);
}
.kindsof {
  display: flex;
  align-items: center;
}
.kindsof li {
  margin-left: 30px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(52, 52, 52, 1);
  cursor: pointer;
}
.kindsof li:hover {
  color: rgb(28, 128, 243);
}
.kindsof li:first-child {
  margin-left: 0;
}
.kindsof li.blue {
  color: rgb(28, 128, 243);
}
.blue {
  color: rgba(17, 123, 241, 1);
}
.allcourses {
  width: 1520px;
  margin: 0 auto;
}
.recomeEach {
  display: flex;
  flex-wrap: wrap;
}
.recomeEach li {
  width: 350px;
  margin-top: 40px;
  margin-left: 30px;
  cursor: pointer;
  border: 1px solid #ededed;
  /* box-sizing: border-box; */
  padding: 0 0 15px 0;
}
.recomeEach li:hover {
  border-color: #f40;
}
.recomeEach li:nth-child(4n + 1) {
  margin-left: 0;
}
.coursecover {
  position: relative;
  width: 350px;
  height: 240px;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.3);
  overflow: hidden;
}
.coursecover img {
  width: 100%;
  height: 100%;
  transition: all 0.3s;
}
.coursecover img:hover {
  transform: scale(1.2);
}
.courseback {
  position: absolute;
  width: 285px;
  height: 50px;
  line-height: 50px;
  text-align: right;
  background: linear-gradient(
    90deg,
    rgba(0, 0, 0, 0.05) 0%,
    rgba(0, 0, 0, 0.6) 100%
  );
  bottom: 0;
  left: 0;
}
.intro {
  font-size: 24px;
  font-family: PingFangSC-Semibold, PingFang SC;
  font-weight: 600;
  color: rgba(255, 255, 255, 1);
  letter-spacing: 1px;
  padding-right: 40px;
}
.course_title {
  padding: 15px 0 0 10px;
  font-size: 20px;
  font-family: PingFangSC-Medium, PingFang SC;
  font-weight: 500;
  color: rgba(52, 52, 52, 1);
  line-height: 28px;
  letter-spacing: 1px;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
.course_title:hover {
  color: rgba(17, 123, 241, 1);
}
.price_time {
  height: 40px;
  padding: 0 10px 0 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 6px;
}
.price {
  padding: 2px 0 0 10px;
  font-size: 24px;
  font-family: PingFangSC-Medium, PingFang SC;
  font-weight: 500;
  color: rgba(241, 17, 64, 1);
  letter-spacing: 1px;
}
.price span {
  color: #999;
}
.time {
  padding-top: 7px;
  color: #999;
}
.recomcourse {
  padding: 14px 0 14px 20px;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 4px solid rgba(17, 123, 241, 1);
}
.coursetitle {
  font-size: 24px;
  font-family: PingFangSC-Semibold, PingFang SC;
  font-weight: 600;
  color: rgba(17, 123, 241, 1);
  letter-spacing: 1px;
}
</style>