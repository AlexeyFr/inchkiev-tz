<template>
    <main class="main">
        <aside class="aside">
            <div class="links">
                <a class="svg-wrap" @click="$emit('state', 'start')">
                        <img src="../assets/img/home.svg" alt="home">
                    </a>
                <!-- можно вернутся назад и выбрать другой препарат -->
                <a class="svg-wrap" @click="back">
                    <img src="../assets/img/back.svg" alt="refresh">
                </a>
            </div>
            <div class="params">
                <h2>Параметри:</h2>
                <div class="medicine">
                    <div v-for="medicin in medicins" :key="medicin.kind" :class="['item', medicin.kind]">
                        <img :src="require(`../assets/img/${medicin.kind}.svg`)" :alt="medicin.kind" />
                        <span class="count">{{(patients.filter(patient => patient.recipe == medicin.kind)).length}}</span>
                    </div>
                </div>
            </div>
            <div class="queue">
                <div>Осталось в очереди:</div>
                <span class="curent">{{patient + 1}}</span>
                <span>/</span>
                <span>{{patients.length}}</span>
            </div>
        </aside>
        <section class="choice-screen">
            <div class="content" v-touch:swipe.left="swipeLeft" v-touch:swipe.top="swipeTop" v-touch:swipe.right="swipeRight" v-touch:swipe.bottom="swipeBottom">
                <div :class="['card', patients[patient].recipe]">
                    <img :src="require(`../assets/img/patients/${patients[patient].img}`)" alt="foto" />
                    <div class="patient">
                        <h3 class="name-age">{{patients[patient].name}}, {{patients[patient].age}} років</h3>
                        <div class="info">{{patients[patient].info}}</div>
                    </div>
                    <div v-if="patients[patient].recipe" :class="['choice', patients[patient].recipe]">
                        <span>{{medicins.find(medicin => medicin.kind == patients[patient].recipe).name}}</span>
                    </div>
                </div>
                <div class="btns">
                    <a v-for="medicin in medicins" :key="medicin.name" :class="['btn', medicin.kind]" @click="recipe(medicin.kind)">
                        <span>{{medicin.name}}</span>
                    </a>
                </div>
            </div>
        </section>
    </main>
</template>

<script>
export default {
    name: 'ChoiceMedicine',
    props: ['patients', 'medicins'],
    data() {
        return {
            patient: 0,
            isDisabled: false,
        }
    },
    methods: {
        back() {
            if (this.patient > 0) {
                this.patient--;
                this.patients[this.patient].recipe = null;
            }
        },
        recipe(kind) {
            if (!this.isDisabled) {
                this.isDisabled = !this.isDisabled;
                this.patients[this.patient].recipe = kind;
                setTimeout(() => {
                    if (this.patient < this.patients.length - 1) {
                        this.patient++;
                    } else {
                        this.$emit('state', 'result')
                    }
                    this.isDisabled = !this.isDisabled;
                }, 700)
            }
        },
        swipeLeft() {
            this.recipe('sad')
        },
        swipeTop() {
            this.recipe('happy')
        },
        swipeRight() {
            this.recipe('heart')
        },
        swipeBottom() {
            this.back();
        },
    }
}
</script>
