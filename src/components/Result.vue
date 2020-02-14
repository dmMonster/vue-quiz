<template>
    <div>
        <div>
            Your score: <span v-bind:class="{'result-good': goodResult, 'result-bad': !goodResult}">{{result}} </span>
        </div>
        <button v-on:click="restart" class="button-restart">Restart</button>
    </div>
</template>

<script>
    export default {
        name: "Result",
        props: ["result", "questionNumber"],
        data() {
            return {
                goodResult: false,
            }
        },
        methods: {
            restart() {
                this.$emit("restart-quiz");
            }
        },

        mounted() {
            if(this.result/this.questionNumber > 0.6){
                this.goodResult = true;
            }
        }

    }
</script>

<style scoped lang="scss">
    .button-restart {
        font-weight: bold;
        text-transform: capitalize;
        width: 8em;
        height: 4em;
        background-image: linear-gradient(90deg, #2f89ff, #602dff);
        border: none;
        border-radius: 2em;
        color: white;
        cursor: pointer;
        margin: 1em;
    }
    .button-restart:hover {
        box-shadow: 1px 1px 10px black;
    }

    .result-bad {
        color: #b43d1b;
        font-weight: bold;
        font-size: 350%;
    }

    .result-good {
        color: #12641b;
        font-weight: bold;
        font-size: 550%;
    }
</style>