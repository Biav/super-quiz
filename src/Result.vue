<template>
    <div class="result">
        <div class="panel" :class="{'panel-success': total, 'panel-danger': !total}">
            <div class="panel-heading">
                <h3 class="panel-title"> {{ title }}</h3>
            </div>
            <div class="panel-body">
                {{ result }}
                <button class="btn btn-sm btn-default" @click="back(total)">Voltar</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ["total"],
        methods: {
            back(total) {
                this.$emit('voltar', total);
            }
        },
        computed: {
            title() {
                return (this.total > 0) ? "Right Answer" : "Wrong Answer";
            },
            result() {
                return (this.total > 0) ? "The result is: " + this.total : " Try again";
            }
        }
        
    }
</script>


<style scoped>
    .result {
        display: flex;
        justify-content: center;
    }

    .panel {
        width: 50%;
        margin-top:40px;
        text-align: center;
    }

    button {
        display: block;
        margin: 0 auto;
        margin-top: 20px;
    }
</style>
