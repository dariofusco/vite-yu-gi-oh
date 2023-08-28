<script>
import axios from "axios";

export default {

    data() {
        return {
            cards: [],
            archetype: [],
            searchArchetype: "",
        };
    },
    methods: {
        fetchCards() {
            const url = `https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${this.searchArchetype}`;
            axios
                .get(url)
                .then((response) => {
                    this.cards = response.data.data;
                    console.log(response.data.data);
                });
        },
        fetchArchetype() {
            const url = "https://db.ygoprodeck.com/api/v7/archetypes.php";
            axios
                .get(url)
                .then((response) => {
                    this.archetype = response.data;
                    console.log(response.data)
                })
        }
    },
    mounted() {
        //this.fetchCards();
        this.fetchArchetype();
    },
};
</script>

<template>
    <div class="container py-2">
        <select class="form-select" v-model="searchArchetype" @change="fetchCards">
            <option disabled value>Selezione carte da cercare</option>
            <option v-for="singleArchetype in archetype">{{ singleArchetype.archetype_name }}</option>
        </select>
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