<template>
    <ul>
            <li v-for='item in items' :key='item.id'>
                    <div class= 'quote'>"{{ item.quote }}" -- {{ item.source }} in </div>
                    <div class='character'>{{ item.context }}</div>
                <br>
                <br>

            </li>
        </ul>
</template>

<script>
import data from './json/quotes.json'

export default {
  name: 'QuotesList',
  data(){
      return {
          items: data
      }
  }
}
</script>

<style scoped>
    .quote {
        display: inline;
    }
    .character{
        display: inline;
        font-style: italic;
    }
</style>
