<template>
    <h2>Look for an advice:</h2>
    <input type="text" :value="search"
        @input="search = $event.target.value" />
    <button @click="getDataByQuery">Discover!</button>
    <div v-if="adviceByQuery.message">
        <p id="notice">{{adviceByQuery.message.text}}</p>
    </div>
    <div v-else>
        <p v-for="item in adviceByQuery.slips" :key="item.id">{{item.advice}}</p>
    </div>
</template>

<script>
export default {
    name: 'ByQuery',
    data() {
        return {
            adviceByQuery: [],
            search: null
        }
    },
    methods: {
        async getDataByQuery() {
            const res = await fetch(`https://api.adviceslip.com/advice/search/${this.search}`);
            const slips = await res.json();
            this.adviceByQuery = slips;
        }
    }
}
</script>

<style scoped>
    #notice {
        font-family: 'Poppins', sans-serif;
    }
</style>