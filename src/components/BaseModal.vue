<template>
    <div class="modal">
        <div class="modal__content">
            <slot />
            <button class="close__btn" type="button" @click.prevent="closeModal">
                <svg width="14" height="13" viewBox="0 0 14 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <line x1="1.35355" y1="0.646447" x2="13.3536" y2="12.6464" stroke="#555555" />
                    <line x1="0.646447" y1="12.6464" x2="12.6464" y2="0.646447" stroke="#555555" />
                </svg>
            </button>
        </div>
        <div>

        </div>
    </div>
</template>

<script>

export default {
    methods: {
        closeModal() {
            this.$emit('closeModal')
        }
    }
}
</script>

<style>
.modal {
    display: flex;
    position: fixed;
    z-index: 4;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    align-items: center;
    justify-content: center;
    background-color: rgba(0, 0, 0, 0.5);
    overflow-y: auto;
}

.modal__content {
    display: flex;
    padding: 45px 40px;
    position: relative;
    z-index: 4;
    min-width: 450px;
    min-height: 200px;
    overflow: auto;
    background-color: #fff;
}

.close__btn {
    position: absolute;
    right: 10px;
    top: 13px;
    border: none;
    background-color: transparent;
    cursor: pointer;
}
</style>