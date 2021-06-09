<template>
  <div class="popup">
    <div class="popup__background"></div>
    <div class="popup__body">
      <div class="popup__header">
        <h2>Налоговый вычет</h2>
        <button class="btn-close" @click="closePopup">
          <img src="../assets/images/close.svg" alt="" />
        </button>
      </div>
      <div class="popup__content">
        <div class="popup__info">
          <p>
            Используйте налоговый вычет чтобы погасить ипотеку досрочно. Размер
            налогового вычета составляет не более 13% от своего официального
            годового дохода
          </p>
        </div>
        <div class="popup-input">
          <h3>Ваша зарплата в месяц</h3>
          <input type="text" class="input-popup" placeholder="Введите данные" 
            v-model.trim="pay"
            :class="payError ? 'input-error' : ''"
          />
          <p class="text-error" v-if="payError">Поле обязательно для заполнения</p>
          <button class="btn-text" @click="calculate">Рассчитать</button>
          <div class="popup__checkbox" v-if="showCalculate">
            <h3>Итого можете внести в качестве досрочных:</h3>
            <Checkbox v-for="(item, index) in arrDeduct" 
                :key="item.id"
                :sumCheck="item"
                :yearCheck="index + 1"
                />
          </div>
        </div>
        <div class="popup-question">
          <h3>Что уменьшаем?</h3>
          <button class="btn-tags">Платёж</button>
          <button class="btn-tags">Срок</button>
        </div>
      </div>
      <button class="btn-big">Добавить</button>
    </div>
  </div>
</template>

<script>
import Checkbox from './Checkbox';

export default {
    data() {
        return {
            showCalculate: false,
            payError: false,
            pay: '',
            formatPay: '',
            arrDeduct: [],
            minDue: 260000,
        }
    },
    methods: {
        closePopup() {
            this.$emit('closePopup');
        },
        calculate() {
            this.count()
            this.isFormatPay()
            
            // console.log(isNaN(this.pay));
            // this.payError = isNaN(this.pay)
        },
        count() {
            this.arrDeduct = []
            let isMinDue = this.minDue
            let check = Number(this.pay) * 12* 0.13
            if (!isNaN(check) && check > 0) {
              for (isMinDue; isMinDue > 0; isMinDue) {
                  if (isMinDue < check) {
                      this.arrDeduct.push(isMinDue)
                      break
                  }
                  isMinDue = isMinDue - check
                  this.arrDeduct.push(check)
              }
              this.payError = false
              //console.log(this.arrDeduct);
              return this.showCalculate = true
            } 
            return this.payError = true
        },
        isFormatPay() {
            this.formatPay = Number(this.pay).toLocaleString('ru-RU')
            this.pay = this.formatPay
        },
    },
    components: {
        Checkbox,
    },
  };
</script>

<style>
.popup {
  position: fixed;
  height: 100vh;
  width: 100vw;
  z-index: 99;
  display: flex;
  justify-content: center;
  align-items: center;
}
.popup__background {
  position: fixed;
  height: 100vh;
  width: 100vw;
  background: rgba(0, 0, 0, 0.3);
  top: 0;
  left: 0;
  z-index: 100;
}
.popup__body {
  z-index: 101;
  min-height: 462px;
  max-height: 100%;

  box-sizing: border-box;
  width: 552px;
  background: #ffffff;
  border-radius: 30px;
  padding: 27px 32px 32px 32px;
  display: flex;
  flex-direction: column;
}
.popup__header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 16px;
}
.popup__content {
  overflow-y: auto;
  flex-grow: 1;
}
.popup__info {
  margin-bottom: 24px;
  padding-right: 40px;
}
.popup-input {
  position: relative;
  margin-bottom: 24px;
}

.input-popup {
  margin: 0;
  outline: none;
  border: 1px solid #dfe3e6;
  box-sizing: border-box;
  border-radius: 3px;
  width: 100%;
  height: 40px;
  padding: 8px 10px;
  margin-top: 8px;
  margin-bottom: 8px;
}
.input-error {
    border: 1px solid #EA0029;
}
.text-error {
    font-style: normal;
    font-weight: normal;
    font-size: 10px;
    line-height: 12px;
    color: #EA0029;
}

.popup-question {
  display: flex;
  margin-bottom: 40px;
}
.popup-question h3 {
    margin-right: 76px;
}

.popup__checkbox {
  margin-top: 16px;
}

.btn-close {
  position: relative;
  text-decoration: none;
  background: transparent;
  height: 18px;
  width: 18px;
  background: none;
  border: 1px solid #fff;
  cursor: pointer;
}

.btn-close img {
  position: absolute;
  top: 0;
  left: 0;
}

.btn-text {
  background: transparent;
  text-decoration: none;
  border: 1px solid #fff;
  cursor: pointer;
  color: #ea0029;
  font-style: normal;
  font-weight: 600;
  font-size: 14px;
  line-height: 24px;
  padding: 0;
}
.btn-text:hover {
  color: #f53a31;
}
.btn-text:active {
  color: #ea0029;
}

.btn-big {
  width: 100%;
  height: 56px;
  line-height: 24px;
  cursor: pointer;
  color: #fff;
  border: 1px solid #ff5e56;
  font-style: normal;
  font-size: 16px;
  line-height: 24px;
  background: linear-gradient(
      255.35deg,
      #dc3131 0.83%,
      rgba(255, 79, 79, 0) 108.93%
    ),
    #ff5e56;
  box-shadow: 0px 0px 24px rgba(234, 0, 41, 0.33);
  border-radius: 6px;
}
.btn-big:hover {
  background: #ea0029;
}

.btn-tags {
  margin-right: 16px;
  font-style: normal;
  font-size: 14px;
  line-height: 24px;
  color: #000;
  background: #eef0f2;
  border: 1px solid #eef0f2;
  border-radius: 50px;
  padding: 6px 12px;
  cursor: pointer;
}
.btn-tags:hover {
  background: #dfe3e6;
}
.btn-tags:active {
  background: linear-gradient(
      255.35deg,
      #dc3131 0.83%,
      rgba(255, 79, 79, 0) 108.93%
    ),
    #ff5e56;
  color: #fff;
}

/* Media */
@media (max-width: 800px) {
 
  .popup__info {
    padding-right: 35px;
  }
}

@media (max-width: 570px) {
  .popup__body {
    width: 100%;
    height: 100%;
    left: 0;
    margin-left: 0;
    margin-top: 0;
    border-radius: 0;
    padding: 22px 22px 16px 16px;
  }
  .popup__header h2 {
    font-size: 18px;
    line-height: 24px;
  }
  .btn-close {
    height: 12px;
    width: 12px;
  }
  .btn-close img {
    height: 12px;
    width: 12px;
  }
  .popup__info {
    padding-right: 0;
    font-size: 12px;
  }
  .popup__checkbox {
    margin-top: 24px;
  }
  .popup__checkbox h3 {
    padding-right: 30px;
  }
  .btn-big {
    font-size: 12px;
    line-height: 16px;
  }
}

@media (max-width: 400px) {
    .popup-question {
        margin-bottom: 40px;
        flex-wrap: wrap;
    }
    .popup-question h3 {
        margin-right: 176px;
        margin-bottom: 24px;
    }
}
</style>
