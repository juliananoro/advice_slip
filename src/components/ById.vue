<template>
    <div>
        <input placeholder="0" type="number" :value="slip_id"
            @input="slip_id = $event.target.value" />
        <button @click="getDataById">Choose</button>
        <p v-if="adviceById != null">{{adviceById.slip.advice}}</p>
        <p id="message" v-if="slip_id > 224">This number is too high!</p>
    </div>
    
</template>

<script>
export default {
    name: 'ById',
    data() {
        return {
            adviceById: null,
            slip_id: null
        }
    },
    methods: {
        async getDataById() {
            const res = await fetch(`https://api.adviceslip.com/advice/${this.slip_id}`);
            const slip = await res.json();
            this.adviceById = slip;
        }
    }
}
</script>

<style scoped>
    div {
        display: grid;
        grid-template-areas:
            "input . button"
            "p p p";
        grid-template-columns: 1fr 3fr;
    }
     input {
        width: 80%;
        border-radius: 8px;
        font-size: 20px;
        text-align: center;
     }

    button {
        background-color: #4b2f64;
        color: white;
        height: 50px;
        width: 100%;
        border-radius: 8px;
        font-family: 'Macondo', sans-serif;
        font-size: 20px;
    }

    button:hover {
        transform: scale(102%) perspective(4px);
    }

    p {
        margin-top: 4%;
        grid-column: span 3;
    }

    #message {
       font-family: 'Poppins', sans-serif; 
    }
</style>