<script setup>
import {ref} from 'vue'

let count = ref(100);

function doThing(){
    count.value ++
    console.log(count)
    
}

</script>


<template>
    Example
    <button @click="doThing">Increment</button>
    <div>
        {{ count }}
    </div>
</template>