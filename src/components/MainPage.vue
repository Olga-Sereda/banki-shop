<template>
    <main>
        <div class="container cards__container">
            <h2 class="main__title">Картины эпохи Возрождения</h2>
            <ul class="cards-list">
                <CardItem v-for="card in cards" :key="card.id" :card="card" />
            </ul>
        </div>
    </main>
</template>

<script>
import CardItem from './CardItem.vue';

export default {
    props: ['cards'],
    components: { CardItem }
}
</script>