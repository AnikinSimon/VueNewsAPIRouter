<template>
    <v-container class="grey lighten-5">
        <v-row no-gutters>

            <NewsModul v-for="(item, i) in news" v-bind:key="i" v-bind:image="item.urlToImage" v-bind:link="item.url"
                v-bind:title="item.title">
                {{ item.description }}
            </NewsModul>

        </v-row>
    </v-container>
</template>

<script>
import NewsModul from '../components/NewsModul.vue'
export default {

    name: 'RusLan',
    components: {
        NewsModul
    },
    data() {
        return {
            news: []
        }
    },
    methods: {
        getNews() {
            this.axios({
                method: 'GET',
                url: "https://newsapi.org/v2/top-headlines?country=ru&apiKey=d7f41a32c26b4bbfb596d58b1a54c766"
            }).then((response) => {
                console.log(response)
                this.news = response.data.articles;
            })
        }
    },
    mounted() {
        this.getNews();
        console.log("RUS")
    }
}
</script>
