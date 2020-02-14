<template>
    <div>
        <h2>{{quizTitle}}</h2>
        <hr>
        <div v-if="!showResult">
            <h4>Question number: {{questionNumber + 1}}</h4>
            <Question v-on:selectAnswer="selectAnswer" v-bind:question="questions[questionNumber]"></Question>
        </div>
        <Result v-on:restart-quiz="restart" v-if="showResult" v-bind:result="result" v-bind:questionNumber="questionNumber"></Result>
    </div>
</template>

<script>
    import Question from "@/components/Question";
    import Result from "@/components/Result";

    export default {
        name: "Quiz",
        components: {Result, Question},
        data() {
            return {
                quizTitle: "Simple Quiz",
                questionNumber: 0,
                result: 0,
                showResult: false,
                questions: [
                    {
                        title: "Test question 1",
                        answers: {
                            a: "answer A correct",
                            b: "answer B",
                            c: "answer C",
                            d: "answer D",
                        },
                        correct: "a",
                    },
                    {
                        title: "Test question 2",
                        answers: {
                            a: "answer A",
                            b: "answer B",
                            c: "answer C",
                            d: "answer D correct",
                        },
                        correct: "d",
                    },
                    {
                        title: "Test question 3",
                        answers: {
                            a: "answer A",
                            b: "answer B correct",
                            c: "answer C",
                            d: "answer D",
                        },
                        correct: "b",
                    },
                    {
                        title: "Test question 4",
                        answers: {
                            a: "answer A",
                            b: "answer B correct",
                            c: "answer C",
                            d: "answer D",
                        },
                        correct: "b",
                    },
                    {
                        title: "Test question 5",
                        answers: {
                            a: "answer A",
                            b: "answer B correct",
                            c: "answer C",
                            d: "answer D",
                        },
                        correct: "b",
                    },
                    {
                        title: "Test question 6",
                        answers: {
                            a: "answer A",
                            b: "answer B",
                            c: "answer C correct",
                            d: "answer D",
                        },
                        correct: "c",
                    },
                    {
                        title: "Test question 7",
                        answers: {
                            a: "answer A",
                            b: "answer B",
                            c: "answer C",
                            d: "answer D correct",
                        },
                        correct: "d",
                    }
                ]
            }
        },
        methods: {
            selectAnswer: function(correct) {
                if(correct){
                    this.result++;
                }

               if(this.questionNumber >= this.questions.length-1) {
                   this.showResult = true;
               }else {
                   this.questionNumber++;
               }

            },

            restart: function() {
                this.result = 0;
                this.questionNumber = 0;
                this.showResult = false;
            }
        }
    }
</script>

<style scoped>

</style>