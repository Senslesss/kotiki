<template>
    <v-app class="app">
        <div class="wrapper">
            <v-container>
                <h1 class="h1">Ты сегодня покормил кота?</h1>
                <div class="carts">
                    <cart v-for="(items, index) in cards"
                          :key="index"
                          :type="items.type"
                          :weight="items.weight"
                          :unit="items.unit"
                          :quantity="items.quantity"
                          :present="items.present"
                          :happy="items.happy"
                          :question="items.question"
                          :sentenceDefault="items.sentenceDefault"
                          :sentenceHover="items.sentenceHover"
                          :questionHover="items.questionHover"
                          :disableStatus="items.disableStatus"
                    />
                </div>
            </v-container>
        </div>
    </v-app>
</template>

<script>
    import cart from "./components/cart/cart";

    export default {
        name: 'App',

        components: {
            cart
        },

        data: () => ({
            cards: [
                {
                    type: 'c фуа-гра',
                    weight: '0,5',
                    unit: 'кг',
                    quantity: '10 порций',
                    present: 'мышь в подарок',
                    happy: '',
                    question: 'Сказочное заморское явство',
                    questionHover: 'Котэ не одобряет?',
                    sentenceDefault: 'Чего сидишь? Порадуй котэ,',
                    sentenceHover: 'Печень утки разварная с артишоками',
                    disableStatus: true,

                },
                {
                    type: 'c рыбой',
                    weight: '2',
                    unit: 'кг',
                    quantity: '40 порций',
                    present: '2 мыши в подарок',
                    happy: '',
                    question: 'Сказочное заморское явство',
                    questionHover: 'Котэ не одобряет?',
                    sentenceDefault: 'Чего сидишь? Порадуй котэ,',
                    sentenceHover: 'Головы щучьи с чесноком да свежайшая сёмгушка.',
                    disableStatus: false,

                },
                {
                    type: 'c курой',
                    weight: '5',
                    unit: 'кг',
                    quantity: '100 порций',
                    present: '5 мышей в подарок',
                    happy: 'заказчик доволен',
                    question: 'Сказочное заморское явство',
                    questionHover: 'Котэ не одобряет?',
                    sentenceDefault: 'Чего сидишь? Порадуй котэ,',
                    sentenceHover: 'Филе из цыплят с трюфелями в бульоне.',
                    disableStatus: false,
                },
            ]
        }),
    };
</script>

<style lang="scss" scoped>
    @font-face {
        font-family: 'TrebuchetMS';
        src: url('./assets/fonts/TrebuchetMS-Bold.eot');
        src: local('☺'), url('./assets/fonts/TrebuchetMS-Bold.woff') format('woff'),
        url('./assets/fonts/TrebuchetMS-Bold.ttf') format('truetype'),
        url('./assets/fonts/TrebuchetMS-Bold.svg') format('svg');
        font-weight: 700;
        font-style: normal;
    }

    @font-face {
        font-family: 'TrebuchetMS';
        src: url('./assets/fonts/TrebuchetMS.eot');
        src: local('☺'), url('./assets/fonts/TrebuchetMS.woff') format('woff'),
        url('./assets/fonts/TrebuchetMS.ttf') format('truetype'),
        url('./assets/fonts/TrebuchetMS.svg') format('svg');
        font-weight: 400;
        font-style: normal;
    }

    @font-face {
        font-family: 'Exo2';
        src: url('./assets/fonts/Exo2.0-Thin.eot');
        src: local('☺'), url('./assets/fonts/Exo2.0-Thin.woff') format('woff'),
        url('./assets/fonts/Exo2.0-Thin.ttf') format('truetype'),
        url('./assets/fonts/Exo2.0-Thin.svg') format('svg');
        font-weight: 100;
        font-style: normal;
    }

    * {
        font-family: 'TrebuchetMS', sans-serif;
    }

    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0;
    }

    .wrapper {
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        background: url("./assets/images/bg.jpg");
        box-shadow: inset 0px 20px 150px 20px black;
    }

    .carts {
        width: 100%;
        display: flex;
        justify-content: space-between;
        @media (max-width: 1264px) {
            flex-wrap: wrap;
        }
    }

    .h1 {
        font-family: 'Exo2', sans-serif;
        font-size: 36px;
        font-weight: 100;
        margin-bottom: 25px;
        color: white;
    }
</style>
