<template>
  <div class="main">
    <!-- 轮播图 -->
    <div class="swiper-container lunbo">
      <div class="swiper-wrapper"
           id="bannerList">
        <div class="swiper-slide"><img src="https://img-qn-2.51miz.com/Element/00/72/92/36/de18663c_E729236_74043100.jpg!/quality/90/unsharp/true/compress/true/format/jpg/fh/320"
               alt=""></div>
        <div class="swiper-slide"><img src="https://img-qn-0.51miz.com/preview/photo/00/01/59/41/P-1594102-CFAC8CCF.jpg!/quality/90/unsharp/true/compress/true/format/webp/fh/320"
               alt=""></div>
        <div class="swiper-slide"><img src="https://img-qn-4.51miz.com/Element/00/72/92/83/79530673_E729283_bfef6e75.jpg!/quality/90/unsharp/true/compress/true/format/jpg/fh/320"
               alt=""></div>
      </div>
      <div class="swiper-pagination"></div>
      <div class="swiper-button-prev colorsprev"></div>
      <!--左箭头。如果放置在swiper-container外面，需要自定义样式。-->
      <div class="swiper-button-next colorsprev"></div>
      <!--右箭头。如果放置在swiper-container外面，需要自定义样式。-->
    </div>
    <div class="allcourses">
      <div class="recomment">
        <div class="recomcourse">
          <span class="coursetitle"> 热门推荐</span>
          <div class="more">
            <router-link to="/header/recoment">
              <span>更多</span>
              <img src="../assets/image/more.png"
                   alt="">
            </router-link>
          </div>
        </div>
        <div class="row row-feature mfw-acc-hide row-bg">
          <div class="wrapper">
            <!-- 热门推荐 -->
            <el-row :gutter="20">
              <el-col :span="8"
                      v-for="(item,index) in hotData"
                      :key="item.uuid">
                <el-card shadow="hover"
                         body-style="{background:' #e5e9f2'}">
                  <div class="first"
                       @click="toRecomentDetail(item.uuid)">
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
            <div class="other"
                 @click="toMore">
              更多推荐<i class="el-icon-top-right"></i>
            </div>
          </div>
        </div>
      </div>
      <div class="recomment twicerecomment">
        <!-- 游记攻略 -->
        <div class="messages">
          <div class="recomcourse">
            <span class="coursetitle">游记攻略</span>
            <div class="more">
              <router-link to="/header/message">
                <span>更多</span>
                <img src="../assets/image/more.png"
                     alt="">
              </router-link>
            </div>
          </div>
          <ul class="messageEach">
            <div class="content">
              <div class="guide-list">
                <el-card shadow="hover"
                         v-for="(item,index) in StrategyData"
                         :key="item.uuid">
                  <div class="item clearfix"
                       @click="toStrategy(item.uuid)">
                    <div class="img"><img :src="item.sale"></div>
                    <div class="detail">
                      <h3>{{item.name}}超实用攻略，找个周末去爬山赏水喝茶</h3>
                      <ul>
                        <li>{{item.name}}景区分类有哪些？</li>
                        <li>{{item.tag}}</li>
                      </ul>
                      <div class="extra">
                        <span class="el-icon-location">{{item.label[0]}}</span>
                        <span class="el-icon-view">{{item.hot}}</span>
                      </div>
                    </div>
                  </div>
                </el-card>
                <!-- 分页器 -->
                <el-pagination small
                               background=true
                               layout="prev, pager, next"
                               :total="50">
                </el-pagination>
              </div>
            </div>
          </ul>
        </div>
        <!-- 游记分享 -->
        <div class="share">
          <div class="recomcourse">
            <span class="coursetitle">游记分享</span>
            <div class="more">
              <router-link to="/header/share">
                <span>更多</span>
                <img src="../assets/image/more.png"
                     alt="">
              </router-link>
            </div>
          </div>
          <ul class="messageEach">
            <div class="tn-list">
              <el-card shadow="hover"
                       v-for="(item,index) in travelsData"
                       :key="item.uuid"
                       :body-style="{ padding: '9px 10px' }">
                <div class="tn-item clearfix"
                     @click="toShare(item.uuid)">
                  <div class="tn-image">
                    <a href="/i/23505421.html"
                       target="_blank">
                      <img class="lazy"
                           data-original="http://note.mafengwo.net/img/49/f7/fe36f3e18f26d84c459e74579d8464fc.jpeg"
                           width="155"
                           height="100"
                           :alt="item.name"
                           :src="item.sale"
                           style="display: inline;">
                    </a>
                  </div>
                  <div class="tn-wrapper">
                    <dl>
                      <dt>
                        <div href="/i/23505421.html"
                             class="title-link"
                             target="_blank">{{item.name}}</div>
                      </dt>
                      <dd>
                        <div href="/i/23505421.html"
                             class="introduction"
                             target="_blank">{{item.introduction}}...</div>
                      </dd>
                    </dl>
                    <div class="tn-extra">
                      <span class="tn-user"><a href="/u/62315564.html"
                           target="_blank"
                           rel="nofollow"><img src="http://p1-q.mafengwo.net/s12/M00/5D/73/wKgED1uzW7yAF9aKAAB7L9TyvMQ31.jpeg?imageMogr2%2Fthumbnail%2F%2116x16r%2Fgravity%2FCenter%2Fcrop%2F%2116x16%2Fquality%2F90">从我的全中国路过</a></span>
                    </div>
                  </div>
                </div>
              </el-card>
            </div>
            <!-- 分页器 -->
            <el-pagination small
                           background=true
                           layout="prev, pager, next"
                           :total="50">
            </el-pagination>
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
import Swiper from '../assets/script/swiper.min.js'
export default {
  name: '',
  inject: ['reload'],
  data () {
    return {
      loginbool: false,
      jingqus: [],
      shares: [],
      label: '',
      hotData: [],
      StrategyData: [],
      travelsData: [],
      params: {}
    }
  },
  methods: {
    toMore () {
      this.$router.push({ name: 'recoment', query: this.params })
      window.scrollTo(0, 0)
    },
    toRecomentDetail (params) {
      this.$router.push({ name: 'recomdetails', query: { uuid: params } })
    },
    toStrategy (params) {
      this.$router.push({ name: 'strategydetail', query: { uuid: params } })
    },
    toShare (params) {
      console.log(params);
      this.$router.push({ name: 'sharedetails', query: { uuid: params } })
    },
    changelb () {
      this.loginbool = !this.loginbool
    },
    jingqu () {
      this.$axios.get('travel/getjingqus').then(res => {
        if (res) {
          res.data.data.forEach(item => {
            this.$set(item, 'showscal', false)
          })
          this.jingqus = res.data.data
        }
      })
    },
    // 移入移出图片放大
    enter (item) {
      this.$set(item, 'showscal', true)
    },
    leave (item) {
      this.$set(item, 'showscal', false)
    },
    share () {
      this.$axios.get('travel/shares').then(res => {
        if (res) {
          this.shares = res.data.data
        }
      })
    },
    jump (item) {
      localStorage.setItem('viewdetails', JSON.stringify(item))
      this.$router.push('/header/recomdetails')
    },
    jumpshare (item) {
      this.$router.push('/header/sharedetails')
    }
  },
  mounted () {
    // 热门推荐
    this.params.label = this.$route.query.label
    console.log(this.params.label);
    if (this.params.label == undefined) {
      // 调随机景区接口
      this.$axios.get('/travel/randomTravel').then(res => {
        if (res.data) {
          this.hotData = res.data.data.slice(0, 6)
        }
      })
    } else {
      this.$axios.post('/travel/getTravelByLabel', this.params).then(res => {
        console.log(res);
        if (res.data) {
          this.hotData = res.data.data.slice(0, 6)
        }
      })
    }
    // 攻略
    this.$axios.get('/travel/randomTravel').then(res => {
      if (res.data) {
        this.StrategyData = res.data.data.slice(0, 6)
      }
    })
    // 游记分享
    this.$axios.get('/travel/randomTravel').then(res => {
      if (res.data) {
        this.travelsData = res.data.data.slice(0, 6)
      }
    })
    this.jingqu()
    this.share()
    var mySwiper = new Swiper('.swiper-container', {
      loop: true,
      speed: 300,
      autoplay: {
        delay: 3000
      },
      // 分页器（圆点）
      pagination: {
        el: '.swiper-pagination',
        clickable: true, //点击圆点切换
      },
      // 前进后退按钮
      navigation: {
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev',
      },
    })
  },
  watch: {
    'showlogin': function (newVal, oldVal) {
      if (newVal) {
        this.changelb()
      }
    }
  },
  computed: {
    showlogin () {
      return this.$route.params.showlogin
    }
  },
}
</script>

<style scoped lange="less">
@import "../assets/cssC/swiper.min.css";
.lunbo {
  width: 100%;
  height: 570px;
  cursor: pointer;
}
.lunbo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
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
.coursetitle {
  font-size: 24px;
  font-family: PingFangSC-Semibold, PingFang SC;
  font-weight: 600;
  color: rgba(17, 123, 241, 1);
  letter-spacing: 1px;
}
.more_name {
  display: flex;
  align-items: center;
  font-size: 14px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(52, 52, 52, 1);
  line-height: 20px;
  letter-spacing: 1px;
  cursor: pointer;
}
.more img {
  margin-left: 16px;
  width: 16px;
  height: 16px;
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
  padding: 0 0 15px 0;
  background: #fff;
}
.recomeEach li.on {
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
.recomeEach li.on .coursecover img {
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
.twicerecomment {
  display: flex;
  justify-content: space-between;
}
.twicerecomment > div {
  width: 48%;
}
.messageEach {
  width: 100%;
  box-sizing: border-box;
  margin-top: 30px;
}
.content {
  float: left;
}
.guide-list .item a {
  display: block;
}
.guide-list .img {
  float: left;
  display: inline;
  width: 220px;
  height: 150px;
  position: relative;
  overflow: hidden;
}
.guide-list .detail {
  margin-left: 235px;
  height: 150px;
  position: relative;
}
.guide-list .detail h3 {
  margin-bottom: 10px;
}
.guide-list .detail h3:hover {
  color: #ff9d00;
}
.guide-list .detail ul {
  margin-bottom: 20px;
}
.guide-list .detail .extra {
  position: absolute;
  bottom: 0;
}
.detail .extra span {
  margin-right: 100px;
}
.createtime {
  padding-top: 20px;
}
.messageEach li > img {
  width: 100px;
  height: 100x;
  border-radius: 4px;
}
.title_content:hover {
  color: rgba(17, 123, 241, 1);
}
.introduction {
  margin: 15px 0;
  width: 100%;
  height: 60px;
  /* 文字开头空格 */
  text-indent: 2em;
  font-size: 10px;
  line-height: 15px;
  text-overflow: ellipsis;
  word-break: break-all;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
}
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
.tn-item {
  padding: 13px 0;
  height: 150px;
  position: relative;
}
.tn-image {
  float: left;
  width: 220px;
  height: 150px;
  overflow: hidden;
  position: relative;
}
.tn-wrapper {
  float: right;
  width: 450px;
}
.title-link {
  font-weight: bold;
}
.title-link:hover {
  color: #ff9d00;
}
.tn-extra .tn-ding {
  float: right;
  color: #ff9d00;
  font-size: 14px;
  width: 100px;
  text-align: right;
}

.tn-extra .tn-user {
  position: absolute;
  bottom: 10px;
}

body {
  -webkit-text-size-adjust: 100%;
  font-size: 12px;
  font-family: Arial, "Lucida Grande", "Microsoft Yahei", "Hiragino Sans GB",
    "Hiragino Sans GB W3", SimSun, "PingFang SC", STHeiti;
  color: #666;
  margin: 0;
  word-wrap: break-word;
  padding: 40px 0;
  min-width: 980px;
  border-bottom: 1px solid #e4e4e4;
  background-color: #fafafa;
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
.other {
  text-align: center;
  width: 100%;
  height: 50px;
  font-size: 20px;
  color: rgb(248, 192, 7);
  margin-top: 30px;
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
.el-pagination {
  margin-top: 10px;
  height: 30px;
  text-align: center;
}
</style>