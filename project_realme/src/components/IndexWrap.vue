<template>
  <div class="title_div">

    <van-row type="flex" justify="space-between" style='padding:0 .2rem;'>
      <!-- 搜索框 -->
      <van-col @click='searchBtnFn' span="20" class='search_div'>
        <van-icon name="search" class='search_icon' size='.5rem' />
        <span>真我GT2 Pro</span>
      </van-col>
      <!-- 按钮 -->
      <van-col span="3">
        <van-icon name="comment-o" class='messageBtn'/>
      </van-col>
    </van-row>

      
    <!-- 轮播图 -->
    <van-swipe class="my-swipe" :autoplay="4000" indicator-color="white">
        <van-swipe-item v-for='n in swipe_imgArr'>
          <img :src='n' />
        </van-swipe-item>
    </van-swipe>


    <!-- 7天无理由退货 -->
    <div class='indexServicePolicy'>
      <ul>
        <li>7天无理由退货</li>
        <li>30天换货保障</li>
        <li>顺丰包邮</li>
        <li id='dip'>正品保障</li>
      </ul>
    </div>

  <!-- 商品栏目按钮列表 -->
  <div class='goodsColumn_wrap'>
      <van-grid :column-num="5">
        <van-grid-item 
          v-for="(n,inx) in goodsColumn_Arr" 
          :key=inx 
          :icon=n.img_url
          :text=n.img_txt
          >
          </van-grid-item>
      </van-grid>
  </div>


  <!-- 春节不打烊 -->
  <div>
    <img src='../assets/1.jpg'></img>
  </div>

  <!-- 限时优惠 -->
    <div class='CountDownWrap'>
      <p>限时优惠</p>
      <van-count-down :time="time_val" class='CountDownStyle'>
        <template v-slot="timeData">
          <span class="time_block">{{ timeData.hours }}</span>
          <span class="colon">:</span>
          <span class="time_block">{{ timeData.minutes }}</span>
          <span class="colon">:</span>
          <span class="time_block">{{ timeData.seconds }}</span>
        </template>
      </van-count-down>
      <a href="#" class='right'>更多>></a>
    </div>

    <!-- 限时优惠商品列表 -->
    <div class='GoodsList_wrap'>
        <van-grid :column-num="2" :gutter="1" >
          <van-grid-item 
            v-for="(n,inx) in goodsListObj" 
            :key=inx 
            :icon=n.img_url
            :text=n.img_txt
            >
            </van-grid-item>
        </van-grid>
    </div>

    <footer_bar></footer_bar>

  </div>
</template>

<script>
import '../assets/resetVant.css'
import axios from 'axios'
import footer_bar from './footer_bar'

export default {
  name: 'IndexWrap',
  data(){
    return {
      active:'',
      tabBtnArr:[],
      swipe_imgArr:[
        
        require('@/assets/2.jpg'),
        require('@/assets/3.jpg'),
        require('@/assets/4.jpg'),
        require('@/assets/5.jpg'),
        require('@/assets/6.jpg'),
        require('@/assets/7.jpg'),
        require('@/assets/8.jpg'),
        require('@/assets/9.jpg'),

      ],
      time_val: 30 * 60 * 60 * 1000,
      goodsColumn_Arr:[
      {
        img_url:require('@/assets/p1.png'),
        img_txt:'手机'
      },{
        img_url:require('@/assets/p2.png'),
        img_txt:'耳机手表'
      },{
        img_url:require('@/assets/p3.png'),
        img_txt:'手机周边'
      },{
        img_url:require('@/assets/p4.png'),
        img_txt:'电脑办公'
      },{
        img_url:require('@/assets/p5.png'),
        img_txt:'潮玩生活'
      },{
        img_url:require('@/assets/p6.png'),
        img_txt:'新品快报'
      },{
        img_url:require('@/assets/p7.png'),
        img_txt:'会员福利'
      },{
        img_url:require('@/assets/p8.png'),
        img_txt:'组队抢'
      },{
        img_url:require('@/assets/p9.png'),
        img_txt:'年货节'
      },{
        img_url:require('@/assets/p10.png'),
        img_txt:'以旧换新'
      }
            ],
      goodsListObj:[{
        img_url:'https://r1.realme.net/general/20211230/1640834892904.png',
        img_txt:'￥2599'
      },{
        img_url:'https://r1.realme.net/general/20220104/1641301259164.png',
        img_txt:'￥3699'
      },{
        img_url:'https://r1.realme.net/general/20220104/1641301987833.png',
        img_txt:'￥2699'
      },{
        img_url:'https://r1.realme.net/general/20211019/1634615903271.png',
        img_txt:'￥1799'
      },{
        img_url:'https://r1.realme.net/general/20210922/1632293326946.png',
        img_txt:'￥2099'
      },{
        img_url:'https://r1.realme.net/general/20211105/1636104662892.png',
        img_txt:'￥2499'
      }]
    }
  },
  created(){
      
     

    
  },
  components:{footer_bar},
  methods:{
    // 搜索框
    searchBtnFn(){
      this.$router.push('/searchPage');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title_div{
  padding: .23rem 0 .23rem 0;
}
.logo{
  width: 1.84rem;height: .53rem;margin-top: .1rem;
}
.messageBtn{
  width: .98667rem;height: .53333rem;font-size: .8rem;
  line-height: .53333rem;
  text-align: center;
  color: #aaa;
  
  background: #fff;margin: .1rem 0 0 0;
}
.search_div{
  font-size: .4rem;
  height: .75rem;
  background-color: #ededed;color: #666;
  border-radius: .11rem;
  display: flex;
  justify-content: center; 
  align-items: center;
}
.search_icon{
  margin:0 .2rem 0 0;
}

.tabBtnWrap{
  font-size: .35rem;padding:  0 .2rem;
}

.my-swipe .van-swipe-item {
  height: 16rem;
  color: #fff;
  font-size: 20px;
  line-height: 150px;
  text-align: center;
  background-color: #fff;
  margin-top:.4rem;
  
}

.indexServicePolicy{
  width: 100%;
}
.indexServicePolicy ul{
  height: .96rem;
  padding: 0 .4rem;
  display: flex;
  align-items: center;
}
.indexServicePolicy ul li{
  flex: 1;
  float: left;
  border-right: solid .03rem #000;
  text-align: center;
  font-size: .32rem;
  color: #333;
  margin-left: .10667rem;
  line-height: .42667rem;
  display: inline-block;
  vertical-align: middle;
}
#dip{border-right:none;}

.indexServicePolicy ul li i{
  width: .42667rem;
  height: .42667rem;
  display: inline-block;
  vertical-align: middle;
  font-size: .32rem;
  color: #333;
  margin-left: .10667rem;
  line-height: .42667rem;
  display: inline-block;
  vertical-align: middle;
  background-size: 100% 100%;
}
.goodsColumn_wrap{
  /*font-size: 1rem;*/
}

/* 倒计时 */
.CountDownWrap{
  height: 1.33333rem;
  overflow: hidden;
  padding: 0 .4rem;
  line-height: 1.33333rem;
  background: #fff;
}
.CountDownWrap p{
  float: left;font-size: .42667rem;
}
.CountDownWrap a.right{
  float: right;font-size: .37333rem;color: #333;
}


.colon {
  display: inline-block;
  margin: 0 4px;
  font-size: .5rem;
  color: #333;
}
.time_block {
  display: inline-block;
  width: .48rem;height: .48rem;
  color: #fff;
  font-size: .32rem;
  text-align: center;
  background-color: #ee0a24;
  border-radius: .05333rem;
  line-height: .48rem;
}

.CountDownStyle{
  float: left;margin: 32px 0 0 21px;
}

.GoodsList_wrap{
  margin-bottom: 1rem;
}


</style>
