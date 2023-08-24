<script>
import TheHeader from "./components/TheHeader.vue";
import TheFooter from "./components/TheFooter.vue";
import CardsList from "./components/CardsList.vue"
export default {
    components: {
        TheHeader,
        TheFooter,
        CardsList,
    }
}
</script>

<template>
<TheHeader></TheHeader>
<main>
<CardsList></CardsList>
</main>
<TheFooter></TheFooter>
</template>

<style lang="scss">
main {
    background-color: #d3853a;
}
</style>
