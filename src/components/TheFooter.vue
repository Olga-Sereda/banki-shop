<template>
    <div>
        <footer>
            <div class="container footer__container">
                <NavigationPage class="nav__gray" />
                <ul class="socials-list">
                    <li class="social-item social-pic1">
                        <p>+7 (812) 555-55-55</p>
                    </li>
                    <li class="social-item social-pic2">
                        <p>г. Санкт-Петербург, ул. Ефимова, 3</p>
                    </li>
                </ul>
            </div>
        </footer>
    </div>
</template>

<script>
import NavigationPage from './NavigationPage.vue';

export default {
    components: { NavigationPage }
}
</script>