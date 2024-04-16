<template>
    <div v-if="posts">
        <v-data-table 
        v-model:items-per-page="itemsPerPage"
        :headers="headers"
        :items="data"
        item-value='userId'
        class='elevation-1'
        >

        </v-data-table>
    </div>
</template>

<script>
    import { VDataTable } from "vuetify/labs/components";
    import getAllPost from "../services/getAllPost.js";

    export default{
        components: {
            VDataTable
        },
        
        setup() {
            const { posts, error, load } = getAllPost()
            load()
            return { 
                posts, 
                error, 
                load, 
                itemsPerPage: 10, 
                headers: [
                    {
                        title: 'User ID',
                        align: 'start',
                        sortable: false,
                        key: 'userId'
                    },
                    {
                        title: 'Title',
                        align: 'start',
                        key: 'title'
                    },
                    {
                        title: 'Body',
                        align: 'start',
                        key: 'body'
                    }
                ],
                data: posts

            }
        }
    }

</script>

<style>
    
</style>