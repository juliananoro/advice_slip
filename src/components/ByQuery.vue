<template>
    <div id="search">
       <input type="text" placeholder="Search for an advice..." :value="search"
        @input="search = $event.target.value" />
        <button @click="getDataByQuery">Discover!</button> 
    </div>
    <div v-if="adviceByQuery.message">
        <p id="notice">{{adviceByQuery.message.text}}</p>
    </div>
    <ol v-else>
        <li v-for="item in adviceByQuery.slips" :key="item.id">{{item.advice}}</li>
    </ol>
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

    input {
        height: 50px;
        font-size: 20px;
        font-family: 'Macondo', sans-serif;
        border-radius: 8px;
        text-align: center;
        margin-right: 20px;
    }

    button {
        background-color: #4b2f64;
        color: white;
        height: 50px;
        width: 150px;
        border-radius: 8px;
        font-family: 'Macondo', sans-serif;
        font-size: 20px;
    }

    button:hover {
        transform: scale(102%) perspective(4px);
    }

    #search {
        padding: 20px;
    }

    p, li {
        padding: 10px;
        font-size: 20px;
    }
</style>