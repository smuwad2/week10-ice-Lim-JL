<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        data(){
            return{
                imagepath:''
            }
        },
        props:{
            subject:String,
            entry:String,
            mood:String
        },
        computed:{
            imagepath(){
                return `/public/assets/${this.mood.toLowerCase()}.png`
            }
        }
    }
</script>


<template>
    <!-- TODO: add your template code here. Use boostrap card --> 
    <div class="card" style="width: 18rem;">
        <img class="card-image-top" :src=imagepath>
        
        <div class="card-body">
            <div class="card-title text-center">
                <h4>{{ subject }}</h4>
             </div>
            <div class="card-text">
                {{ entry }}
            </div>
        </div>
    </div>

</template>

