<template>
    <label class="checkbox">
        <input class="checkbox__input" type="checkbox">
        <span class="check__box"></span>
        <span class="check">{{sumCheck.toLocaleString('ru-RU')}} рублей</span><p>{{setInStr}} {{yearCheck}}-{{setYearStr}} год</p>
    </label>
    <hr>
</template>

<script>
export default {
    props: {
        sumCheck: {
            type: Number,
        },
        yearCheck: {
            type: Number,
        },
    },
    data() {
        return {
            yearStr: 'ый',
            yearIn: 'в',
        }
    },
    computed: {
        setInStr() {
            if (this.yearCheck === 2) {
                return 'во'
            }
            return this.yearIn
        },
        setYearStr() {
            let isYearCheck = String(this.yearCheck)
            if ((isYearCheck.length === 1) && (isYearCheck[0]) === '2') {
                return 'ой'
            } else if ((isYearCheck.length > 1) && (isYearCheck[1]) === '2') {
                return 'ой'
            } else if ((isYearCheck[0]) === '3' && (isYearCheck[1]) === '3' || (isYearCheck[isYearCheck.length - 1]) === '3' && (isYearCheck[0]) !== '1') {
                return 'ий'
            } else if ((isYearCheck[0]) >= '6' && (isYearCheck[0]) < '9' || (isYearCheck[1]) >= '6' && (isYearCheck[1]) < '9') {
                return 'ой'
            } else if ((isYearCheck[0]) === '4' && (isYearCheck[1]) === '0') {
                return 'ой'
            }
            return this.yearStr
        }
    }
}
</script>

<style scoped>
    .checkbox {
        display: flex;
        margin-top: 18px;
        margin-bottom: 18px;
        height: 20px;
    }
    .checkbox > p {
        line-height: 20px;
        margin:0;
        text-align:center;
        padding: 0;
    }
    .checkbox > span {
        line-height: 20px;
        text-align:center;
        padding: 0;
    }
    .checkbox__input {
        border: 0;
        margin: 0;
        display: block;
        left: 0;
        height: 20px;
        width: 20px;
        margin-right: 12px;
        border-radius: 6px;

        position: absolute;
        appearance: none;
        -webkit-appearance: none;
        -moz-appearance: none;
    }
    .check {
        margin-left: 32px;
        margin-right: 3px;
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 24px;
        color: #000;
    }
    .check__box {
        cursor: pointer;
        position: absolute;
        height: 20px;
        width: 20px;
        background-image: url('../assets/images/checkboxNormal.svg');     
    }

    /* Checked */

    .checkbox__input:checked + .check__box {
        background-image: url('../assets/images/checkboxClick.svg');
    }
    .checkbox__input:hover + .check__box {
        background-image: url('../assets/images/checkboxHover.svg');
    }
    .checkbox__input:checked:hover + .check__box {
        background-image: url('../assets/images/checkboxHoverChecked.svg');
    }
</style>