<template>
    <div>
        <button @click="getData">Take a card!</button>
        <p v-if="randomAdvice != null">{{randomAdvice.slip.advice}}</p>    
    </div> 
</template>

<script>
export default {
    name: 'Random',
    data() {
        return {
            randomAdvice: null
        }
    },
    methods: {
        async getData() {
            const res = await fetch("https://api.adviceslip.com/advice");
            const slip = await res.json();
            this.randomAdvice = slip;
        }
    }
}
</script>

<style scoped>
    div {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    button {
        background-color: #4b2f64;
        color: white;
        height: 50px;
        width: 100%;
        border-radius: 12px;
        font-family: 'Macondo', sans-serif;
        font-size: 20px;
    }

    button:hover {
        transform: scale(102%) perspective(4px);
    }

    p {
        margin-top: 4%;
    }
</style>