<template>
    <div class="container">
        <h2>Quotes Added</h2>
        <progress-bar :num-quotes="numQuotes"></progress-bar>
        <quote-input class="row"></quote-input>
        <div class="row">
            <div v-for="(quote, index) in quotes" class="col-sm-3">
                <quote-card  :quote-text="quote" @quoteWasRemoved="removeQuote(index)"></quote-card>
            </div>
        </div>
    </div>
</template>

<script>
    import ProgressBar from './components/ProgressBar.vue';
    import QuoteInput from './components/QuoteInput.vue';
    import {eventBus} from "./main";
    import QuoteCard from './components/QuoteCard.vue';

    export default {
        data() {
            return {
                numQuotes: 0,
                quotes: []
            }
        },
        methods: {
            removeQuote(index) {
                this.quotes.splice(index, 1);
                this.numQuotes--;
            }
        },
        components: {
            ProgressBar, QuoteInput, QuoteCard
        },
        created() {
            eventBus.$on('quoteWasAdded', quote => {
               if (this.numQuotes < 10) {
                   this.numQuotes++;
                   this.quotes.push(quote);
                   console.log(quote);
               } else {
                   alert('Quotes has reached maximum');
               }
            });
        }
    }
</script>

<style>

</style>
