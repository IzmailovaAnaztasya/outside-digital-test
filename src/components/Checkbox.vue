<template>
    <label class="checkbox">
        <input class="checkbox__input" type="checkbox">
        <span class="check__box"></span>
        <span class="check">{{sumCheck.toLocaleString('ru-RU')}} рублей</span><p>в {{yearCheck}}-{{yearStr}} год</p>
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
        yearStr: {
            type: String,
        },
    },
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