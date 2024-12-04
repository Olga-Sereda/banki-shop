<template>
    <div>
        <header>
            <div class="container header__container">
                <NavigationPage />
                <form class="form" @submit.prevent="sumbit">
                    <input type="text" placeholder="Поиск по названию картины" v-model="currentNameCard">
                    <button>Найти</button>
                </form>
            </div>
        </header>
    </div>
</template>

<script>
import NavigationPage from './NavigationPage.vue';

export default {
    data() {
        return {
            currentNameCard: ''
        }
    },
    props: ['nameCard'],
    components: { NavigationPage },
    watch: {
        nameCard(value) {
            this.currentNameCard = value
        }
    },
    methods: {
        sumbit() {
            this.$emit('update:nameCard', this.currentNameCard)
        }
    },
}

</script>