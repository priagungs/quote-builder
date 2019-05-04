<template>
    <div @click="removeQuote">
        <h4>{{ QuoteText }}</h4>
    </div>
</template>

<script>
    export default {
        name: "QuoteCard",
        props: {
            QuoteText: String
        },
        methods: {
            removeQuote() {
                console.log('remove');
                this.$emit('quoteWasRemoved');
            }
        }
    }
</script>

<style scoped>
    div {
        margin: 10px auto;
        border: 1px solid black;
        padding: 10px;
    }

    div:hover {
        background: rgba(255, 0, 0, 0.2);
        cursor: pointer;
    }

    h4 {
        font-family: Arizona;
        font-style: italic;
    }
</style>