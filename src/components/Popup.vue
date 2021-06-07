<template>
    <trasition name="fade">
        <div class="popup">
        </div>
    </trasition>
    <trasition name="slide">
        <div class="popup__body">
            <div class="popup__header">
                <h2>Налоговый вычет</h2>
                <button class="btn-close" @click="closePopup">
                    <img src="../assets/images/close.svg" alt="">
                </button>
            </div>
            <div class="popup__info">
                <p>Используйте налоговый вычет чтобы погасить ипотеку досрочно. Размер налогового вычета составляет
                 не более 13% от своего официального годового дохода</p>
            </div>
            <div class="popup-input">
                <h3>Ваша зарплата в месяц</h3>
                <input type="text" name="" id="" placeholder="Введите данные">
                <button class="btn-text">Рассчитать</button>
                <div class="popup__checkbox">
                    <h3>Итого можете внести в качестве досрочных:</h3>
                    <Checkbox />
                    <Checkbox />
                    <Checkbox />
                    <Checkbox />
                </div>
            </div>
            <div class="popup-question">
                    <h3>Что уменьшаем?</h3>
                    <button class="btn-tags">Платёж</button>
                    <button class="btn-tags">Срок</button>
            </div>
                <button class="btn-big">Добавить</button>
        </div>
    </trasition>
</template>

<script>
import Checkbox from './Checkbox'

export default {
    methods: {
        closePopup() {
            this.$emit('closePopup')
        }
    },
  components: {
    Checkbox
  }
}
</script>

<style>
    .popup {
        position: fixed;
        height: 100%;
        width: 100%;
        background: rgba(0, 0, 0, 0.3);
        top: 0;
        left: 0;
        z-index: 2;
    }
    .popup__body {
        position: fixed;
        left: 50%;
        margin-left: -276px;
        margin-top: 120px;
        z-index: 3;

        box-sizing:border-box;
        width: 552px;
        min-height: 476px;
        background: #FFFFFF;
        border-radius: 30px;
        padding: 27px 32px 32px 32px;
    }
    .popup__header {
        display: flex;
        justify-content: space-between;
        margin-bottom: 16px;
    }
    .popup__info {
        margin-bottom: 24px;
        padding-right: 40px;
    }
    .popup-input {
        position: relative;
        margin-bottom: 24px;
    }
    .popup-input input {
        margin: 0;
        outline: none;
        border: 1px solid #DFE3E6;
        box-sizing: border-box;
        border-radius: 3px;
        width: 100%;
        height: 40px;
        padding: 8px 10px;
        margin-top: 8px;
        margin-bottom: 8px;
    }
    .popup-question {
        display: flex;
        height: 36px;
        margin-bottom: 40px;
    }
    .popup__checkbox {
        margin-top: 16px;
    }

    .btn-close{
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
        color: #EA0029;
        font-style: normal;
        font-weight: 600;
        font-size: 14px;
        line-height: 24px;
        padding: 0;
    }
    .btn-text:hover {
        color: #F53A31;
    }
    .btn-text:active {
        color: #EA0029;
    }

    .btn-big {
        width: 100%;
        height: 56px;
        line-height: 24px;
        cursor: pointer;
        color: #fff;
        border: 1px solid #FF5E56;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 24px;
        background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
        box-shadow: 0px 0px 24px rgba(234, 0, 41, 0.33);
        border-radius: 6px;
    }
    .btn-big:hover {
        background: #EA0029;
    }
  
    .btn-tags {
        margin-right: 16px;
        font-style: normal;
        font-size: 14px;
        line-height: 24px;
        color: #000;
        background: #EEF0F2;
        border: 1px solid #EEF0F2;
        border-radius: 50px;
        padding: 6px 12px;
        cursor: pointer;
    }
    .btn-tags:hover {
        background: #DFE3E6;
    }
    .btn-tags:active {
        background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
        color: #fff;
    }

    /* Animate */
    .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
    }
    .fade-enter, .fade-leave-to {
    opacity: 0;
    }

    .slide-enter-active, .slide-leave-active {
    transition: all .5s;
    }
    .slide-enter, .slide-leave-to {
    transform: translateX(-100px);
    }

    /* Media */
    @media (max-width: 800px) {
        .popup__body {
            width: 453px;
            margin-left: -226px;
        }
        .popup__info {
            padding-right: 35px;
        }
    }

    @media (max-width: 670px) {
        .popup__body {
            margin-top: 20px;
        }
    }

    @media (max-width: 570px) {
        .popup__body {
            width: 100%;
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
</style>