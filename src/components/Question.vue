<template>
    <div>
        <transition name="fade">
            <div v-if="showQuestion">
                <h4>{{question.title}}</h4>
                <ul>
                    <li class="question-answer" v-on:click="selectAnswer(key)" v-for="(answer, key) in question.answers">
                        <span class="key">{{key}}</span>.{{answer}}
                    </li>
                </ul>
            </div>
        </transition>

    </div>
</template>

<script>
    export default {
        name: "Question",
        props: ["question"],
        data() {
            return {
                showQuestion: true,
            }
        },
        methods: {
            selectAnswer(key) {
                if (key === this.question.correct) {
                    this.$emit("selectAnswer", true);
                } else {
                    this.$emit("selectAnswer", false);
                }


                this.showQuestion = false;
                setInterval(() => {
                    this.showQuestion = true;
                }, 500)
            }
        }
    }
</script>

<style scoped lang="scss">
    .question-answer {
        list-style-type: none;
        background-color: rgba(0, 0, 0, 0.1);
        padding: 1em;
        margin-bottom: 1em;
        border-radius: 10%;
        cursor: pointer;
    }

    .question-answer:hover {
        box-shadow: 2px 2px 20px black;
    }

    .key {
        text-transform: uppercase;
        font-weight: bold;
    }

    .fade-leave-active {
        transition: all 300ms;


    }

    .fade-leave-to {
        opacity: 0;
        transform: perspective(500px) translateZ(-200px);
    }

    .fade-enter {
        opacity: 0;
        transform: perspective(500px) translateZ(-200px);
    }
    .fade-enter-active{
        transition: all 300ms;
    }
    .fade-enter-to {
        opacity: 1;
        transform: perspective(500px) translateZ(0);
    }
    .selected {
        background-color: #ffeb94;
    }
</style>