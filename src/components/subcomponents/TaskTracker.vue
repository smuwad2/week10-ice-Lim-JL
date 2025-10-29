<script>
    // TODO: Complete the code
    export default { 
        data() {
            return {
                
            }
        },
        props:{
            task :Object,
            idx:Number
        },
        emits:['removeTask']
        // Hint: insert properties task (Object) and idx (Number)
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
   <div class="card" style="width:18rem; display:inline-block">
    <div class="card-body">
        <div class="card-title">
            Deadline: {{ task.deadline }}
        </div>
        <p class="card-text">
            {{ task.desc }}
        </p>
        <button class="btn btn-primary" @click="$emit('removeTask',idx)">Done</button>
    </div>
   </div>
</template>


