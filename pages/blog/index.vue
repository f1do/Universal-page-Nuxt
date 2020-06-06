<template>
  <b-container>
    <b-row>
        <b-col md-3 v-for="(itm, ndx) in items" :key="ndx">
            <h2>
                <nuxt-link :to="`/blog/${itm.id}`">{{itm.description}}</nuxt-link>
            </h2>
        </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
    data(){
        return{
            items:[
                {id:1, description:'Item #1'},
                {id:2, description:'Item #2'},
                {id:3, description:'Item #3'},
                {id:4, description:'Item #4'}
            ]
        }
    }
}
</script>