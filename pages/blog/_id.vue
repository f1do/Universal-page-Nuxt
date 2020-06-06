<template>
    <b-container>
        <b-card class="mt-2">
            <b-card-body>
                <h1>{{item.title}}</h1>
                <small>{{item.name}}</small>
                <p>
                    {{item.body}}
                </p>
                <nuxt-link to="/blog" class="btn btn-info">go back</nuxt-link>
            </b-card-body>
        </b-card>
    </b-container>
</template>

<script lang="ts">
import Vue from 'vue';
import axios from 'axios';

export default Vue.extend({
    data(){
        return{
        }
    },
    async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
        var item = {name:String};
        try {
            const res = await axios.get(`http://jsonplaceholder.typicode.com/posts/${params.id}`);
            if(res && res.data){
                item = res.data;
                const user = await axios.get(`http://jsonplaceholder.typicode.com/users/${item.userId}`);
                item.name = user.data.name;
            }
            else{
                const e = 'Sorry, no data for this search.';
                console.log(e);
                throw new Error(e);
            }
            return {item};
        } catch (err) {
            console.log(err);
            return err;
        }
    }
});

</script>