<template>
  <b-container class="mt-5">
    <b-card class="mt-2" v-for="(itm, ndx) in items" :key="ndx">
        <b-card-body >
            <nuxt-link :to="`blog/${itm.id}`">
                <h1>{{itm.title}}</h1>
            </nuxt-link>
            <p>
                {{itm.body}}
            </p>
        </b-card-body>
    </b-card>
  </b-container>
</template>

<script lang="ts">
import Vue from 'vue'
import axios from "axios";

export default Vue.extend({
    data(){
        return{
            items:[
            ]
        }
    },
    async created(){
        try {
            const res = await axios.get('http://jsonplaceholder.typicode.com/posts?_limit=10');
            this.items = res.data;
        } catch (err) {
            console.log(err);
        }
    }
})
</script>