<template>
    <main class="main">
        <section class="result-screen">
            <a class="svg-wrap" @click="$emit('state', 'start')">
                <img src="../assets/img/home_white.svg" alt="home">
            </a>
            <img class="result_bg" src="../assets/img/result_screen_bg.png" alt="result bg">
            <div class="content">
                <div class="result">
                    <div v-for="medicin in medicins" :key="medicin.kind">
                        <div class="percent">{{Math.round(((patients.filter(patient => patient.recipe == medicin.kind)).length)*100/patients.length)}}%</div>
                        <div class="name">{{medicin.name}}</div>
                    </div>
                </div>
                <div class="hr"></div>
                <h2>
                    <span>Ваш результат:</span>
                    «Что я здесь делаю?»
                </h2>
                <p>Это тестовое задание, так что не будем углубляться в глубины проблем фармацевтов.</p>
                <a class="btn" @click="$emit('state', 'start')">
                    <span>Попробовать еще</span>
                </a>
            </div>
        </section>
    </main>
</template>

<script>
export default {
    name: 'ResultScreen',
    props: ['patients', 'medicins'],
}
</script>