<template>
    <main class="main">
        <section class="start-screen">
            <div class="content">
                <p>Добро пожаловать в игру</p>
                <h1>
                    <span>Помоги</span> Фармацевту
                </h1>
                <a class="btn" @click="$emit('state', 'choice')">
                    <span>Начать</span>
                </a>
            </div>
        </section>
    </main>
</template>

<script>
export default {
    name: 'StartScreen',
}
</script>
