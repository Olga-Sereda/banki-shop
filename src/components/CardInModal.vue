<template>
    <li class="card__item card__item-modal">
        <a href="#">
            <img :src="card.img" :alt="card.title">
        </a>
        <div class="card__block">
            <h3 class="card__title">
                <a href="">{{ card.title }}</a>
            </h3>
            <div class="card__block-descr">
                <div class="price__block">
                    <span v-if="card.oldPrice" class="price__old">{{ card.oldPrice | numberFormat }} $</span>
                    <span class="price__new">{{ card.price | numberFormat }} $</span>
                </div>
                <button class="card__btn" @click.prevent="addToCard"
                    :class="{ 'card__added-btn': cardAdded, 'card__sending-btn': cardAddSending }">
                    <div v-if="cardAdded" class="card__icon-btn">В корзине</div>
                    <div v-else-if="cardAddSending">Добавляем..</div>
                    <div v-else>Купить</div>
                </button>
            </div>
        </div>
    </li>
</template>

<script>
import numberFormat from '@/helpers/numberFormat';

export default {
    props: ['card'],
    data() {
        return {
            cardAdded: false,
            cardAddSending: false,
        }
    },
    methods: {
        addToCard() {
            this.cardAdded = false;
            this.cardAddSending = true;

            setTimeout(() => {
                this.cardAdded = true;
                this.cardAddSending = false
            }, 1500)
        }
    },
    filters: {
        numberFormat
    }
}
</script>