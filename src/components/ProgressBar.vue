<template>
    <div class="progress">
        <div class="progress-bar" role="progressbar" aria-valuenow="40" aria-valuemin="0" aria-valuemax="10"
             :style="{width: progress + '%'}">
            {{ numQuotes }}/10
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            numQuotes: Number
        },
        computed: {
            progress() {
                return this.numQuotes*10;
            }
        }
    }
</script>
<style scoped>

</style>