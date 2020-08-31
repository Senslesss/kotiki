<template>
    <div class="cart-wrapper">
        <div class="cart"
             @click="changeSelect"
             :class="[{select: selectCart}, {disable: disableStatus}]"
             @mouseenter="changeText"
             @mouseleave="changeTextOut"
        >
            <div class="cart-content">
                <span v-show="!switchTextQuestion" class="question">{{question}}</span>
                <span v-show="switchTextQuestion" class="question">{{questionHover}}</span>
                <h2 class="title-name">Нямушка</h2>
                <span class="type">{{type}}</span>
                <span class="quantity">{{quantity}}</span>
                <span class="present">{{present}}</span>
                <span class="present" v-show="happy">{{happy}}</span>
                <div class="weight-container">
                    <span class="weight">{{weight}}</span>
                    <span class="unit">{{unit}}</span>
                </div>
            </div>
            <div class="disable-wrap" />
        </div>
        <div class="sentence"
             v-show="!switchTextSentence"
             v-if="!disableStatus"
        >
            <span>{{sentenceDefault}}</span>
            <span class="buy"
                  @click="changeSelect"
            >купи.</span>
        </div>
        <div class="sentence"
             v-show="switchTextSentence"
             v-if="!disableStatus"
        >
            <span>{{sentenceHover}}</span>
        </div>
        <div class="sentence yellow--text"
             v-if="disableStatus"
        >
            <span>Печалька, {{type}} закончился.</span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "cart",
        props: {
            type: {
                type: String,
                default: 'No type'
            },
            weight: {
                type: String,
                default: 'No weight'
            },
            unit: {
                type: String,
                default: 'No unit'
            },
            quantity: {
                type: String,
                default: 'No quantity'
            },
            present: {
                type: String,
                default: 'No present'
            },
            happy: {
                type: String,
                default: ''
            },
            question: {
                type: String,
                default: 'No question'
            },
            questionHover: {
                type: String,
                default: 'No question-hover'
            },
            sentenceDefault: {
                type: String,
                default: 'No sentence'
            },
            sentenceHover: {
                type: String,
                default: 'No sentence-hover'
            },
            disableStatus: {
                type: Boolean,
                default: false
            },

        },
        data: () => ({
            selectCart: false,
            switchTextSentence: false,
            switchTextQuestion: false,
        }),
        methods: {
            changeText() {
                if (this.disableStatus === true) {
                    return this.switchTextQuestion = false
                }
                if (this.selectCart === true) {
                    return this.switchTextQuestion = true
                }
            },
            changeTextOut() {
                if (this.disableStatus === true) {
                    return this.switchTextQuestion = false
                }
                if (this.selectCart === true) {
                    return this.switchTextQuestion = false
                }
            },
            changeSelect() {
                this.selectCart = !this.selectCart
                this.switchTextSentence = !this.switchTextSentence
                if (this.selectCart === false) {
                    this.switchTextQuestion = false
                }
            }
        }
    }
</script>

<style lang="scss" scoped>
    .cart {
        height: 480px;
        width: 100%;
        clip-path: polygon(15% 0%, 80% 0%, 100% 0, 100% 80%, 100% 100%, 0 100%, 0% 80%, 0% 10%);
        border: 4px solid #1698d9;
        position: relative;
        border-radius: 10px;
        padding-top: 15px;
        display: flex;
        justify-content: center;
        background-color: white;
        background-image: url("./../../assets/images/bg-cat.png");
        background-size: 366px;
        background-position: -27px 217px;
        cursor: pointer;
        overflow: hidden;


        &:after {
            content: "";
            display: block;
            background: #1698d9;
            width: 33%;
            height: 4px;
            position: absolute;
            left: -16px;
            top: 4px;
            transform: rotate(-45deg);
            @media (max-width: 324px) {
                left: -26px;
                top: 16px;
                transform: rotate(-48deg);
            }
            @media (max-width: 281px) {
                left: -22px;
                top: 16px;
                transform: rotate(-51deg);
            }
        }
        &:hover {
            border: 4px solid #2ea8e6;

            &:after {
                background: #2ea8e6;
            }

            .weight-container {
                background: #2ea8e6;
            }
        }
    }

    .cart-content {
        display: flex;
        flex-direction: column;
        max-width: 215px;
        width: 215px;
    }

    span {
        display: block;
    }

    .question {
        color: #666666;
        width: 100%;
    }

    .title-name {
        font-size: 48px;
        font-weight: bold;

    }

    .type {
        font-size: 24px;
        font-weight: bold;
    }

    .quantity {
        font-size: 14px;
        color: #666666;
        margin-top: 10px;
    }

    .present {
        font-size: 14px;
        color: #666666;
    }

    .weight-container {
        width: 80px;
        height: 80px;
        position: absolute;
        border-radius: 50%;
        background-color: #1698d9;
        right: 12px;
        bottom: 12px;
        color: white;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .weight {
        font-size: 40px;
        position: absolute;
        top: 2px;
        transform: translateX(-50%);
        left: 50%;
    }

    .unit {
        font-size: 18px;
        position: absolute;
        bottom: 2px;
        transform: translateX(-50%);
        left: 50%;
    }

    .cart-wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        max-width: 320px;
        width: 100%;
        margin-bottom: 20px;
        @media (max-width: 1264px) {
            &:nth-child(n+3) {
                margin: 0 auto;
            }
        }
        @media (max-width: 664px) {
            margin: 0 auto;
        }
    }

    .sentence {
        font-size: 13px;
        margin-top: 15px;
        color: white;

        span {
            display: inline;
            margin-right: 5px;
        }

        .buy {
            text-decoration: underline dashed;
            color: #1698d9;
            cursor: pointer;
        }
    }

    .select {
        border: 4px solid #d91667;

        .weight-container {
            background: #d91667;
        }

        &:after {
            background: #d91667;
        }

        &:hover {
            border: 4px solid #e62e7a;

            .weight-container {
                background: #e62e7a;
            }

            &:after {
                background: #e62e7a;
            }
        }
    }

    .disable {
        border: 4px solid #b3b3b3;
        color: #d4d4d4;
        .question,
        .quantity,
        .present {
            color: #d4d4d4;
        }
        &:after {
            background: #b3b3b3;
        }
        .weight-container {
            background: #b3b3b3;
        }

        &:hover {
            border: 4px solid #b3b3b3;

            .weight-container {
                background: #b3b3b3;
            }

            &:after {
                background: #b3b3b3;
            }
        }
        .sentence {
            span {
                color: yellow;
            }
        }

        .disable-wrap {
            position: absolute;
            pointer-events: none;
            width: 100%;
            height: 100%;
            left: 0;
            top: 0;
            background-color: rgba(255, 255, 255, 0.4);
        }
    }

</style>