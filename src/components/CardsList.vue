<script>
import axios from "axios";

export default {
    data() {
        return {
            cards: [],
        };
    },
    methods: {
        fetchCards() {
            const url = "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0";
            axios
                .get(url)
                .then((response) => {
                    this.cards = response.data.data;
                    console.log(response.data.data);
                });
        },
    },
    mounted() {
        this.fetchCards();
    },
};
</script>

<template>
    <div class="container py-2">
        <div class="row">
            <div class="col py-2" v-for="card in cards">
                <div class="card text-center" style="width: 18rem;" v-for="image in card.card_images">
                    <img class="card-img-top" :src="image.image_url" alt="">
                    <div class="card-body">
                        <p class="card-text">{{ card.name }}</p>
                        <span>{{ card.archetype }}</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>