<template>
    <div class="result">
        <div class="panel" :class="{'panel-success': total, 'panel-danger': !total}">
            <div class="panel-heading">
                <h3 class="panel-title"> {{ title }}</h3>
            </div>
            <div class="panel-body">
                {{ result }}
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ["total"],
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
</style>
