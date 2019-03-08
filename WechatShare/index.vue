<template>
  <div
    class="share"
    @touchmove.prevent
  >
    <div class="card_share">
      <div class="card_share_option">
        <div
          class="option_friend"
          @click="shareWechat"
        >
          <img :src="friendImg">
          <p>微信好友</p>
        </div>
        <div
          class="option_moments"
          @click="shareMoments"
        >
          <img :src="shareImg">
          <p>微信朋友圈</p>
        </div>
      </div>
      <div
        class="share_cancel"
        @click="handleCancel"
      >
        <p>取消</p>
      </div>
    </div>
  </div>
</template>

<script>
import friendImg from './icons/icon_share_wechat.svg';
import shareImg from './icons/icon_share_moments.svg';

export default {
  props: {
  },
  data() {
    return {
      friendImg,
      shareImg,
    };
  },
  methods: {
    handleCancel() {
      this.$emit('handleCancel');
    },
    shareWechat() {
      this.$emit('shareWechat');
    },
    shareMoments() {
      this.$emit('shareMoments');
    },
  },
  components: {},
};
</script>

<style lang='scss' scoped>
@keyframes shareAnimation {
  0% {
    transform: translate3d(0, 100%, 0);
    opacity: 0;
  }
  100% {
    transform: translateZ(0);
    opacity: 1;
  }
}
.share {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0px;
  left: 0px;
  z-index: 999;
  background-color: rgba(0, 0, 0, 0.4);
  .card_share {
    position: fixed;
    bottom: 0;
    height: vw(300);
    width: 100%;
    z-index: 99;
    background: #ffffff;
    transform: translate3d(0, 100%, 0);
    animation: shareAnimation 0.4s;
    animation-fill-mode: forwards;
    .card_share_option {
      height: vw(200);
      display: flex;
      width: 100%;
      align-items: center;
      justify-content: center;
      border-bottom: 1px solid #d9d9d9;
      img {
        width: vw(80);
        height: vw(80);
      }
      p {
        margin: 0;
        margin-top: vw(10);
        font-size: vw(24);
        color: #9b9b9b;
      }
      .option_friend,
      .option_moments {
        flex: 1;
        text-align: center;
      }
      .share_cancel {
        display: flex;
        width: 100%;
        height: vw(100);
        align-items: center;
        justify-content: center;
        p {
          font-size: vw(34);
          color: #666666;
        }
      }
    }
  }
}
</style>
