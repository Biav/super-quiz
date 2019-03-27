<template>
    <div class="quiz">
        <div class="panel panel-default">
            <div class="panel-heading">
                <h3 class="panel-title">{{ panelTitle }}</h3>
            </div>
            <div class="panel-body">
                <div class="col-md-6 result" v-for="item in totalQuiz">
<<<<<<< HEAD
                    <button class="btn btn-lg btn-primary" @click="checkResult">{{ item }}</button>
=======
                    <button class="btn btn-lg btn-primary" @click="result(item, $event)">{{ item }}</button>
>>>>>>> 3a1eff54042e38fc3d24c1e855d068b07d33c99d
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                title: 'What is ',
                numberOne: 0,
                numberTwo: 0,
                total: 0,
                results: []
            }
        },
        methods: {
            createNumber(max, min) {
                return  Math.round(Math.random() * (max - min) + min);
            },
            result(item, event) {
                var result = (item === this.total)?true:false;
                this.$emit("result", result, this.total);
            }
        },
        computed: {
            panelTitle() {
                let max = 40;
                let min = 10;

                this.numberOne = this.createNumber(max, min);
                this.numberTwo = this.createNumber(this.numberOne, min);

                this.title = this.title + this.numberOne + ' + ' + this.numberTwo;

                return this.title;
            },
            totalQuiz() {
                this.total = this.numberOne + this.numberTwo;

                this.results.push(this.total);

                for(let i = 0; i < 3; i++) {
                    this.results.push(this.createNumber(this.numberTwo + i, Math.abs(this.numberOne + this.numberTwo) + i));
                }

                this.results.sort(function() { return 0.5 - Math.random() });

                
                return this.results;
            }
        }
    }
</script>


<style scoped>
    .quiz {
        display: flex;
        justify-content: center;
    }

    .panel-default {
        width: 50%;
        margin-top:40px;
        text-align: center;
    }

    .result { 
        padding: 15px;
    }
</style>

