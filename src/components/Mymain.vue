<script >
import SingleCard from './SingleCard.vue'

//importo store
import { store } from '../store'


export default {
    name: "Mymain",

    components: {
        SingleCard
    },

    data() {
        return {
            store,

        }
    },
    computed: {
        numcard() {
            return store.CardList.length;
        }
    }
}




</script>

<template>
    <div class="background">

        <main class="container ">

            <select v-model="store.searchText" class="form-select w-25" id="selected-searchText" @change="$emit('filter')">

                <option selected value="">Selezionare una categoria</option>

                <option v-for="(arch, i) in store.ArchList" :key="i" :value="arch.archetype_name">
                    {{ arch.archetype_name }}
                </option>

            </select>

            <!-- Computed propeties -->
            <div class="count">
                <section v-if="numcard > 0"> trovate {{ numcard }} carte</section>
                <section v-else> ok</section>
            </div>

            <div class="container sub">
                <div class="row row-cols-5 ">
                    <div v-for="card in store.CardList" :key="card" class="col p-2">
                        <SingleCard :info="card" />
                    </div>

                </div>
            </div>

        </main>
    </div>
</template>

<style lang="scss" scoped>
//Scss relativo alla sola sezione di header
@use '../styles/partials/variables' as *;

.background {
    background-color: $bg-color;
}

main {
    padding-top: 50px;
    padding-bottom: 50px;

    select {
        margin-bottom: 20px;
    }

    .count {
        text-align: center;
        margin-bottom: 10px;
        font-weight: bold;
        font-size: 20px;
    }

    .sub {
        background-color: $bg-color1;

    }
}
</style>