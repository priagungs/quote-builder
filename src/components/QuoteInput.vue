<template>
    <div class="flex-center">
        <div class="col-sm-8">
            <p><strong>Quote</strong></p>
            <textarea v-model="quoteText" name="quote" cols="30" rows="5"></textarea>
            <br><br>
            <div class="flex-center">
                <button @click="addQuote" class="btn btn-primary">Add Quote</button>
            </div>
            <br><br>
        </div>
    </div>
</template>

<script>
    import {eventBus} from "../main";

    export default {
        data() {
            return {
                quoteText: ""
            }
        },
        methods: {
            addQuote() {
                if (this.quoteText) {
                    eventBus.$emit('quoteWasAdded', this.quoteText);
                    this.quoteText = "";
                }
            }
        }
    }
</script>

<style scoped>
    .flex-center {
        display: flex;
        justify-content: center;
    }

    button {
        align-items: center;
    }

    textarea {
        width: 100%
    }
</style>