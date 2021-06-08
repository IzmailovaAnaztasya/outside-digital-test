<template>
  <Popup v-if="isPopupVisible" @closePopup="closePopup" />

  <div class="container">
    <button class="btn" @click="showPopup">Налоговый вычет</button>
  </div>
</template>

<script>
import Popup from './components/Popup'

export default {
  data() {
    return {
      isPopupVisible: false
    }
  },
  methods: {
    showPopup() {
      this.isPopupVisible = true
    },
    closePopup() {
      this.isPopupVisible = false
    },
  },
  components: {
    Popup
  }
}
</script>

<style>
  .container {
    display: flex;
    position: fixed;
    top: 50%;
    left: 50%;
    margin-left: -99px;
    margin-top: -28px;
    width: 198px;
    height: 56px;
    padding: 0 auto;
  }

  .btn {
      color: #fff;
      background: transparent;
      border-radius: 6px;
      border: 1px solid #FFFFFF;
      box-sizing: border-box;
      width: 100%;
      height: 100%;

      cursor: pointer;

      font-size: 16px;
      line-height: 24px;
      padding: 12px 32px;
  }
  .btn:hover {
    background: #fff;
    color: #000;
  }

  /* Media */
  @media (max-width: 320px) {
    .container {
      margin-left: -75px;
      margin-top: -20px;
      width: 150px;
      height: 40px;
    }
     .btn {
       font-size: 12px;
       line-height: 16px;

       padding: 12px 23px;
     }   
  }
</style>
