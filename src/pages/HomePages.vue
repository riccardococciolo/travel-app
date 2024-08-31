<script>
import StageCard from '../components/StageCard.vue';
export default {
    components: {
        StageCard
    },
    data() {
        return {
            journeyCount: 1
        };
    },
    methods: {
        addDay() {
            this.journeyCount++;
        }
    }
};
</script>

<template>
    <div>
        <h1 class="text-center p-4">Diario di Viaggio</h1>
        <button class="m-5" @click="addDay">Aggiungi Giornata</button>
        <div class="row p-0 m-0 justify-content-center">
            <StageCard class="col-4" v-for="index in journeyCount" :key="index" />
        </div>
    </div>

</template>

<style lang="scss" scoped></style>