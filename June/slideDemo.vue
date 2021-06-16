<template>
  <load-page :loading="loading" :is-error="isError">
    <template>
      <div class="content-left-wrapper" v-show="currentCard != 1"></div>
      <div class="content-right-wrapper" v-show="currentCard != 8"></div>
      <div class="content-wrapper">
        <div class="card-wrapper" v-for="(item, index) in 8" :key="index">
          <div class="vehicle-card" :style="itemsStyle">
            <div class="top-card">
              <div class="life-circle-card">
                <img src="https://s2.ax1x.com/2019/03/19/AupWvt.jpg" class="img-card"/>
                <div class="card-content">
                  <div class="content-detail">
                    <div class="line-title">颜色</div><div class="line-content">黑色</div>
                  </div>
                  <div class="content-detail">
                    <div class="line-title">类型</div><div class="line-content">汽车</div> 
                  </div>
                  <div class="content-detail">
                    <div class="line-title">品牌</div><div class="line-content">现代</div> 
                  </div>
                </div>
              </div>
            </div>
            <div class="tri-angle">
              <div class="tri-angle-bottom"></div>
              <div class="tri-angle-top"></div>
            </div>
            <div class="dashed-line"></div>
            <div class="circle"></div>
            <div class="life-circle-time">
              <span>2021-06-01 12:23:23</span>
            </div>
          </div>
        </div>
      </div>
      <a-icon 
        v-show="currentCard != 1"
        type="left-circle" 
        class="forward-btn" 
        theme="filled"
        :style="{ fontSize: '68px', color: '#5a575785'}"
        @click="preCard"
      />
      <a-icon 
        v-show="currentCard != 8"
        type="right-circle" 
        class="next-btn" 
        theme="filled" 
        :style="{ fontSize: '68px', color: '#5a575785'}"
        @click="nextCard"
      />
    </template>
    <!-- <a-empty v-else/> -->
  </load-page>
</template>
<script>


export default {
  components: {  },
  computed: {
    itemsStyle() {
      return {
        transform: `translateX(${this.translateX}px)`
      };
    },
  },
  data() {
    return {
      // 当前最左侧卡片序号
      currentCard: 1,
      translateX: 0,
      loading: false,
      isError: false,
    };
  },
  created() {
  
  },
  mounted() {},
  methods: {
    preCard() {
      this.currentCard = this.currentCard - 1
      this.translateX = this.translateX + 230
    },
    nextCard() {
      this.currentCard = this.currentCard + 1
      this.translateX = this.translateX - 230
    }
  },
};
</script>

<style lang="less">
.content-left-wrapper {
  content: '';
  position: absolute;
  width: 10%;
  height: 400px;
  background: linear-gradient(270deg,rgba(255, 255, 255, 0.1),rgba(255, 255, 255, 1));
  z-index: 1;
}
.content-right-wrapper {
  content: '';
  position: absolute;
  width: 8%;
  height: 400px;
  right: 0;
  background: linear-gradient(90deg,rgba(255, 255, 255, 0.1),rgba(255, 255, 255, 1));
  z-index: 1;
}
.content-wrapper {
  display: flex;
  overflow: hidden;
  .card-wrapper {
    width: 230px;
    height: 400px;
    .vehicle-card {
      width: 230px;
      margin: 0 auto;
      transition: all 0.6s ease-in-out;
      .top-card {
        height: 280px;
        padding-left: 26px;
      }
      .img-card {
        width: 145px;
        height: 145px; 
        margin: 17px;
      }
      .life-circle-card {
        border: 1px solid #DBDBDB;
        width: 178px;
        height: 280px;
      }
      .tri-angle {
        display: flex;

      }
      .tri-angle-bottom {
        position: relative;
        width: 0;
        height: 0;
        left: 95px;
        border-width: 20px;
        border-style: solid;
        border-color: #DBDBDB transparent transparent transparent;
      }
      .tri-angle-top {
        width: 0;
        height: 0;
        position: relative;
        content: "";
        left: 56px;
        top: -1px;
        border-width: 19px;
        border-style: solid;
        border-color: #ffffff transparent transparent transparent;
      }
      .card-content {
        display: flex;
        flex-direction: column;
      }
      .content-detail {
        display: flex;
        justify-content: space-between;
      }
      .content-detail:nth-child(n+2){
        margin-top: 12px;
      }
      .line-title {
        margin-left: 17px;
        opacity: 0.4;
        font-size: 14px;
        color: #1E2337;
        letter-spacing: 0;
        font-weight: 400;
      }
      .line-content {
        margin-right: 17px;
        font-size: 14px;
        color: #1E2337;
        letter-spacing: 0;
        text-align: right;
        font-weight: 400;
      }
      .circle {
        border-radius: 50%;
        width: 18px;
        height: 18px;
        background: #3C97FF;
        position: relative;
        z-index: 99;
        bottom: 10px;
        left: 106px;
      }
      .life-circle-time {
        text-align: center;
      }
      .life-circle-time span {
        font-size: 14px;
        color: #1E2337;
        letter-spacing: 0;
        font-weight: 400;
      }
    }
    .dashed-line {
    border: 1px dashed rgba(0,0,0,0.20);
    width: 230px;
    z-index: 0;
    }
  }
}
  .forward-btn {
    position: absolute;
    top: 150px;
    left: 0px;
    z-index: 2;
  }
  .next-btn {
    position: absolute;
    top: 150px;
    right: 0px;  
    z-index: 2;  
  }
</style>
