<template>
    <li class="card__item" :class="{ 'card-disabled': !card.availaible }">
        <a href="#" @click.prevent="showPopup(card.id)">
            <img :src="card.img" :alt="card.title">
        </a>
        <div class="card__block">
            <h3 class="card__title">
                <a @click.prevent="showPopup(card.id)" href="">{{ card.title }}</a>
            </h3>
            <div v-if="!card.availaible" class="card-disabled__text">Продана на аукционе</div>
            <div v-else class="card__block-descr">
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

        <BaseModal v-if="infoModalVisible" @closeModal="closeInfoModal">
            <CardInModal :card-modal-id="currentCardId" :card="card" />
        </BaseModal>
    </li>
</template>

<script>
import numberFormat from '@/helpers/numberFormat';
import BaseModal from './BaseModal.vue';
import CardInModal from './CardInModal.vue';

export default {
    props: ['card'],
    data() {
        return {
            cardAdded: false,
            cardAddSending: false,

            currentCardId: null
        }
    },
    components: { BaseModal, CardInModal },
    methods: {
        addToCard() {
            this.cardAdded = false;
            this.cardAddSending = true;

            setTimeout(() => {
                this.cardAdded = true;
                this.cardAddSending = false
            }, 1500)
        },
        showPopup(cardId) {
            this.currentCardId = cardId
        },
        closeInfoModal() {
            this.infoModalVisible = false
        }
    },
    computed: {
        infoModalVisible: {
            get() {
                return this.currentCardId
            },
            set(isOpen) {
                if (!isOpen) {
                    this.currentCardId = null
                }
            }
        },
    },
    filters: {
        numberFormat
    }
}
</script>