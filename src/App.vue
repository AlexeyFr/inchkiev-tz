<template>
    <div id="app">
        <!-- можно было использовать router, но я обошелся без него -->
        <start-screen v-if="state == 'start'" @state="onState"></start-screen>
        <choice-medicine v-if="state == 'choice'" :patients="patients" :medicins="medicins" @state="onState"></choice-medicine>
        <result-screen v-if="state == 'result'" :patients="patients" :medicins="medicins" @state="onState"></result-screen>
    </div>
</template>

<script>
import "normalize.css"

import StartScreen from './components/StartScreen.vue'
import ChoiceMedicine from './components/ChoiceMedicine.vue'
import ResultScreen from './components/ResultScreen.vue'

export default {
    name: 'App',
    components: {
        StartScreen,
        ChoiceMedicine,
        ResultScreen,
    },
    data() {
        return {
            // я не использовал Vuex, все данные тут
            state: 'start',
            patients: [
                {
                    name: "Валентина",
                    age: 75,
                    img: "1.jpg",
                    info: "Дитя, дай бабусі ліки від тиску за цим рецептом, але не дорогих, тих, що дешевші!",
                    recipe: null,
                },
                {
                    name: "Марія",
                    age: 19,
                    img: "2.jpg",
                    info: "Бабуся приймає брендовий препарат від болю в суглобах, він допомагає, але занадто дорогий. У Вас є якісний аналог з нижчою ціною? Якщо ні — давайте бренд.",
                    recipe: null,
                },
                {
                    name: "Степан",
                    age: 61,
                    img: "3.jpg",
                    info: "Спросоння відсунув гарячий чайник рукою та обпікся. У Вас всі ліки від опіків такі дорогі? Можна хороший препарат недорого?",
                    recipe: null,
                },
                {
                    name: "Любов",
                    age: 58,
                    img: "4.jpg",
                    info: "Лікар призначив препарат від артеріальної гіпертензії, а бренд дорого коштує. Тому мені потрібен аналог з хорошою ефективністю та приємною ціною.",
                    recipe: null,
                },
                {
                    name: "Олександр",
                    age: 20,
                    img: "5.jpg",
                    info: "Порекомендуйте ефективний препарат від болю в горлі за розумну ціну.",
                    recipe: null,
                },
                {
                    name: "Ірина",
                    age: 55,
                    img: "6.jpg",
                    info: "У мене часто невралгії, лікар призначив вітаміни групи В. Мені потрібен якісний аналог за прийнятною ціною.",
                    recipe: null,
                },
            ],
            medicins: [{
                    name: "Препарат 1",
                    kind: "sad"
                },
                {
                    name: "Препарат 2",
                    kind: "happy"
                },
                {
                    name: "Препарат 3",
                    kind: "heart"
                },
            ],
        }
    },
    methods: {
        onState(state) {
            if (state == 'choice') {
                for (let patient of this.patients) {
                    patient.recipe = null;
                }
            }
            this.state = state;
        },
    }
}
</script>

<style lang="scss">
@font-face {
    font-family: "Avenir Next Cyr";
    src: url("./assets/fonts/AvenirNextCyr-Light.eot");
    src: url("./assets/fonts/AvenirNextCyr-Light.eot?#iefix") format("embedded-opentype"),
    url("./assets/fonts/AvenirNextCyr-Light.woff2") format("woff2"),
    url("./assets/fonts/AvenirNextCyr-Light.woff") format("woff"),
    url("./assets/fonts/AvenirNextCyr-Light.ttf") format("truetype"),
    url("./assets/fonts/AvenirNextCyr-Light.svg#AvenirNextCyr-Light") format("svg");
    font-weight: 300;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: "Avenir Next Cyr";
    src: url("./assets/fonts/AvenirNextCyr-Bold.eot");
    src: url("./assets/fonts/AvenirNextCyr-Bold.eot?#iefix") format("embedded-opentype"),
    url("./assets/fonts/AvenirNextCyr-Bold.woff2") format("woff2"),
    url("./assets/fonts/AvenirNextCyr-Bold.woff") format("woff"),
    url("./assets/fonts/AvenirNextCyr-Bold.ttf") format("truetype"),
    url("./assets/fonts/AvenirNextCyr-Bold.svg#AvenirNextCyr-Bold") format("svg");
    font-weight: bold;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: "Avenir Next Cyr";
    src: url("./assets/fonts/AvenirNextCyr-Regular.eot");
    src: url("./assets/fonts/AvenirNextCyr-Regular.eot?#iefix") format("embedded-opentype"),
    url("./assets/fonts/AvenirNextCyr-Regular.woff2") format("woff2"),
    url("./assets/fonts/AvenirNextCyr-Regular.woff") format("woff"),
    url("./assets/fonts/AvenirNextCyr-Regular.ttf") format("truetype"),
    url("./assets/fonts/AvenirNextCyr-Regular.svg#AvenirNextCyr-Regular") format("svg");
    font-weight: normal;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: "Avenir Next Cyr";
    src: url("./assets/fonts/AvenirNextCyr-Medium.eot");
    src: url("./assets/fonts/AvenirNextCyr-Medium.eot?#iefix") format("embedded-opentype"),
    url("./assets/fonts/AvenirNextCyr-Medium.woff2") format("woff2"),
    url("./assets/fonts/AvenirNextCyr-Medium.woff") format("woff"),
    url("./assets/fonts/AvenirNextCyr-Medium.ttf") format("truetype"),
    url("./assets/fonts/AvenirNextCyr-Medium.svg#AvenirNextCyr-Medium") format("svg");
    font-weight: 500;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: "Montserrat";
    src: url("./assets/fonts/Montserrat-Bold.eot");
    src: url("./assets/fonts/Montserrat-Bold.eot?#iefix") format("embedded-opentype"),
    url("./assets/fonts/Montserrat-Bold.woff2") format("woff2"),
    url("./assets/fonts/Montserrat-Bold.woff") format("woff"),
    url("./assets/fonts/Montserrat-Bold.ttf") format("truetype"),
    url("./assets/fonts/Montserrat-Bold.svg#Montserrat-Bold") format("svg");
    font-weight: bold;
    font-style: normal;
    font-display: swap;
}

$white: #ffffff;
$black: #000000;
$teva_dark_gray: #424242;
$purple: #8e9ad5;
$gray_light: #d9d9d9;
$green: #2d8550;
$blue: #5e6ec2;
@mixin letter-spacing {
    letter-spacing: 0.7px;
}

@mixin bg-linear-gradient {
    background: linear-gradient(to right, $green, $blue);
}

body {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-family: "Avenir Next Cyr";
    font-weight: normal;
    font-style: normal;
    line-height: 1.2;
    background-color: $white;
    color: $teva_dark_gray;
}

aside,
section {
    display: block;
    width: 100%;
    min-height: 100vh;
    position: relative;
    z-index: 1;
}

* {
    box-sizing: border-box;
    &:focus {
        outline: none;
    }
}

a {
    display: block;
    text-decoration: none;
    user-select: none;
    cursor: pointer;
}

p,
h1,
h2,
h3 {
    margin: 0;
}

.main {
    display: flex;
}

.btn {
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 100px;
    transition: transform 0.2s;
    &:active {
        transform: translateY(1px);
    }
}

.start-screen {
    background: url("./assets/img/start_screen_bg.jpg") no-repeat center top / cover;
    color: $white;
    .content {
        width: 860px;
        height: 860px;
        @include bg-linear-gradient;
        border-radius: 50%;
        padding: 280px 185px 0 185px;
        margin: -30px 0 0 110px;
        p {
            font-weight: 300;
            font-size: 35px;
            @include letter-spacing;
            text-shadow: 0px 3px 6px $black;
            margin-bottom: 22px;
        }
        h1 {
            font-weight: bold;
            font-size: 70px;
            @include letter-spacing;
            text-transform: uppercase;
            margin-bottom: 114px;
            span {
                display: block;
                font-size: 60px;
                text-transform: capitalize;
                margin-bottom: -5px;
            }
        }
        .btn {
            width: 380px;
            height: 90px;
            font-family: "Montserrat";
            font-weight: bold;
            font-style: normal;
            font-size: 36px;
            color: $purple;
            background: $white;
            margin: 0 auto;
        }
    }
}

.aside {
    width: 32.5%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    @include bg-linear-gradient;
    color: $white;
    z-index: 2;
    .links {
        display: flex;
        padding: 70px 50px;
        .svg-wrap {
            width: 70px;
            height: 70px;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 50%;
            background: $white;
            margin-right: 38px;
            img {
                height: 32px;
            }
        }
    }
    .params {
        padding: 70px 30px 0 40px;
        h2 {
            font-size: 36px;
            font-weight: bold;
            margin-bottom: 30px;
        }
        .medicine {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            .item {
                display: flex;
                justify-content: space-between;
                align-items: center;
                width: 190px;
                height: 80px;
                padding: 0 44px 0 10px;
                background: $white;
                color: $teva_dark_gray;
                border-radius: 40px;
                box-shadow: 0px 0px 50px rgba(131, 42, 64, 0.4);
                margin: 0 auto 38px auto;
                img {
                    width: 60px;
                }
                .count {
                    font-size: 48px;
                    font-weight: bold;
                }
            }
        }
    }
    .queue {
        font-weight: 300;
        @include letter-spacing;
        text-align: center;
        background: rgba(255, 255, 255, 0.15);
        padding: 18px 0;
        div {
            font-size: 35px;
            margin-bottom: 3px;
        }
        span {
            font-size: 45px;
            &.curent {
                font-weight: bold;
            }
        }
    }
}

.choice-screen {
    width: 67.5%;
    overflow: hidden;
    .content {
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        padding: 130px 0 64px 0;
    }
    .card {
        width: 540px;
        min-height: 590px;
        border-radius: 40px;
        overflow: hidden;
        box-shadow: 0px 0px 40px rgba(127, 127, 127, 0.4);
        position: relative;
        img {
            width: 100%;
            margin-bottom: 22px;
        }
        .patient {
            padding: 0 60px;
            .name-age {
                font-size: 32px;
                color: $purple;
                margin-bottom: 6px;
            }
            .info {
                font-weight: 300;
                font-size: 24px;
            }
        }
        .choice {
            width: 360px;
            height: 120px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            font-size: 52px;
            border-width: 8px;
            border-style: solid;
            position: absolute;
            top: 58%;
            left: 50%;
            &.sad {
                color: #8049C7;
                border-color: #8049C7;
                transform: translate(-50%, -50%) rotate(-15deg);
            }
            &.happy {
                color: #169AE4;
                border-color: #169AE4;
                transform: translate(-50%, -50%) rotate(-15deg);
            }
            &.heart {
                color: #FFCA01;
                border-color: #FFCA01;
                transform: translate(-50%, -50%) rotate(15deg);
            }
        }
        &.sad {
            transition: transform 0.6s ease-in;
            transform: translate(-200%, -100%) rotate(-15deg);
        }
        &.happy {
            transition: transform 0.6s ease-in;
            transform: translate(0, -200%) rotate(-15deg);
        }
        &.heart {
            transition: transform 0.6s ease-in;
            transform: translate(200%, -100%) rotate(15deg);
        }
    }
    .btns {
        width: 100%;
        display: flex;
        justify-content: space-between;
        padding: 0px 28px;
        .btn {
            width: 280px;
            height: 90px;
            font-size: 28px;
            font-weight: bold;
            color: $white;
            &.sad {
                background: linear-gradient(to right, #ca57fd, #8049c7);
            }
            &.happy {
                background: linear-gradient(to right, #0cc4fa, #169ae4);
            }
            &.heart {
                background: linear-gradient(to right, #ffd748, #c6c915);
            }
        }
    }
}

.result-screen {
    .svg-wrap {
        width: 70px;
        height: 70px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
        @include bg-linear-gradient;
        position: absolute;
        top: 70px;
        left: 50px;
        z-index: 1;
        img {
            height: 32px;
        }
    }
    .result_bg {
        width: 710px;
        position: absolute;
        top: 0;
        right: 0;
        z-index: 1;
    }
    .content {
        width: 580px;
        margin: 0 130px;
        padding-top: 267px;
        position: relative;
        z-index: 2;
        .result {
            display: flex;
            justify-content: space-around;
            margin-bottom: 59px;
            text-align: center;
            .percent {
                font-size: 48px;
                margin-bottom: 16px;
            }
            .name {
                font-size: 16px;
                font-weight: bold;
            }
        }
        .hr {
            width: 100%;
            height: 2px;
            background: $gray_light;
            margin-bottom: 37px;
        }
        h2 {
            font-size: 46px;
            font-style: bold;
            color: $purple;
            margin-bottom: 10px;
            span {
                display: block;
                font-size: 36px;
                font-weight: 500;
                font-style: normal;
                margin-bottom: -5px;
            }
        }
        p {
            font-size: 24px;
            margin-bottom: 260px;
        }
        .btn {
            width: 270px;
            height: 60px;
            font-size: 24px;
            font-weight: bold;
            color: $white;
            background: linear-gradient(to right, #d9d9d9, #a1a1a1);
        }
    }
}

@media (max-width: 1280px) {
    .start-screen {
        .content {
            width: 430px;
            height: 430px;
            padding: 140px 92px 0 92px;
            margin: -15px 0 0 55px;
            p {
                font-size: 18px;
                text-shadow: 0px 2px 3px $black;
                margin-bottom: 11px;
            }
            h1 {
                font-size: 35px;
                margin-bottom: 56px;
                span {
                    font-size: 30px;
                    margin-bottom: -2px;
                }
            }
            .btn {
                width: 190px;
                height: 45px;
                font-size: 18px;
            }
        }
    }
    .aside {
        .links {
            padding: 35px 25px;
            .svg-wrap {
                width: 35px;
                height: 35px;
                margin-right: 19px;
                img {
                    height: 16px;
                }
            }
        }
        .params {
            padding: 35px 15px 0 20px;
            h2 {
                font-size: 18px;
                margin-bottom: 15px;
            }
            .medicine {
                .item {
                    width: 95px;
                    height: 40px;
                    padding: 0 22px 0 5px;
                    border-radius: 20px;
                    margin-bottom: 19px;
                    img {
                        width: 30px;
                    }
                    .count {
                        font-size: 24px;
                    }
                }
            }
        }
        .queue {
            padding: 9px 0;
            div {
                font-size: 18px;
                margin-bottom: 2px;
            }
            span {
                font-size: 22px;
            }
        }
    }
    .choice-screen {
        .content {
            padding: 65px 0 32px 0;
        }
        .card {
            width: 270px;
            min-height: 295px;
            border-radius: 20px;
            img {
                margin-bottom: 11px;
            }
            .patient {
                padding: 0 30px;
                .name-age {
                    font-size: 16px;
                    margin-bottom: 3px;
                }
                .info {
                    font-size: 12px;
                }
            }
            .choice {
                width: 180px;
                height: 60px;
                font-size: 26px;
                border-width: 4px;
            }
        }
        .btns {
            padding: 0px 14px;
            .btn {
                width: 140px;
                height: 45px;
                font-size: 14px;
            }
        }
    }
    .result-screen {
        .svg-wrap {
            width: 35px;
            height: 35px;
            top: 35px;
            left: 25px;
            img {
                height: 16px;
            }
        }
        .result_bg {
            width: 355px;
        }
        .content {
            width: 290px;
            margin: 0 65px;
            padding-top: 134px;
            .result {
                margin-bottom: 30px;
                .percent {
                    font-size: 24px;
                    margin-bottom: 8px;
                }
                .name {
                    font-size: 12px;
                }
            }
            .hr {
                height: 1px;
                margin-bottom: 19px;
            }
            h2 {
                font-size: 23px;
                margin-bottom: 5px;
                span {
                    font-size: 18px;
                    margin-bottom: -3px;
                }
            }
            p {
                font-size: 12px;
                margin-bottom: 130px;
            }
            .btn {
                width: 135px;
                height: 30px;
                font-size: 12px;
            }
        }
    }
}
</style>
