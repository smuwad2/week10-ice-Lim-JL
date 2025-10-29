<script>
    // Import BlogPost component
    import blogPost2 from './subcomponents/BlogPost2.vue'
	import axios from 'axios'
    export default {
        data() {
            return {
                posts: [] // array of post objects
            }  
        },
        components:{
            blogPost2
        },
        computed: {
            baseUrl() {
                if (window.location.hostname=='localhost')
                    return 'http://localhost:3000' 
                else {
                    const codespace_host = window.location.hostname.replace('5173', '3000')
                    return `https://${codespace_host}`;
                }
            }
        },
        created() { // created is a hook that executes as soon as Vue instance is created
            axios.get(`${this.baseUrl}/posts`)
            .then(response => {
                // this gets the data, which is an array
                this.posts = response.data
                console.log(response.data)
            })
            .catch(error => {
                this.posts = [{ entry: 'There was an error: ' + error.message }]
            })
        },
        methods:{
            deletePost(id){
                axios.get(`${this.baseUrl}/deletePost`,{params:{id}}).then(res=>{
                    console.log(response.data.message)
                    this.post = this.posts.filter(post=>post.id!=id)
                }).catch(error=>{
                    console.error(error)
                })
            }
        }
    }
</script>

<template>
   <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <!-- vfor to insert blogpost components -->
     <blogPost2 v-for="post in posts" :mood="post.mood" :entry="post.entry" :subject="post.subject" :key="post.id">
        <button class="btn btn-primary" @click="deletePost(post.id)">Delete</button>
     </blogPost2>
</template>

