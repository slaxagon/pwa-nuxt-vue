<template>
    <div style ="text-align: center;">
        <h1>You are searching for: {{ message }}</h1>
        <input v-model="message" placeholder="search">
        <button @click = find()>Szukaj</button>
        <div style="display:flex; flex-wrap: wrap; width: 100vw; justify-content: center;">
            <img :src="value.links[0].href" v-for="(value, index) in dataArray" :key ="index" style="width: 100px; height: 100px; object-fit: cover; padding: 5px;"/>
        </div>
    </div>
</template>

<script>
import axios from "axios"
export default {
    name: "index",

    created() {
        this.fetchData("sun"),
        this.message=""
    },

    data() {
        return {
            dataArray: [],
            message: ""
        }

    },

    methods: {
        find(){
        this.fetchData(this.message)
        this.message = ""
        },
       async fetchData(search) {
        await axios.get("https://images-api.nasa.gov/search?q=" + search)
        .then(res => {
            //console.log(res.data.collection.items[0].links[0].href)
            this.dataArray = res.data.collection.items;
        })
        .catch(error => {
            console.log(error)
        })
        }
    }
}
</script>

<style style lang="scss" scoped>

</style>