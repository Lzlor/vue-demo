<template>
    <div>
        <input type="text" v-model="title" @keydown.enter="addTodo">
        <button v-if="active<all" @click="clear">clear</button>
        <ul v-if = "todos.length">
            <li v-for="todo in todos">
                <input type="checkbox" v-model="todo.done">
                <span :class="{done:todo.done}">{{ todo.title }}</span>
            </li>
        </ul>
        <div v-else>暂无数据</div>
        <div>
            全选 <input type="checkbox" v-model="allDone">
            <span>{{ active }}/{{ all }}</span>
        </div>
    </div>
</template>

<script setup>
import { ref,computed,watchEffect } from "vue";

let title = ref("")
let todos = ref([{title:'study',done:false}])
// let todos = ref(JSON.parse(localStorage.getItem('todos')||'[]'))

// watchEffect(()=>{
//     localStorage.setItem('todos',JSON.stringify(todos.value))
// })

function addTodo() {
    todos.value.push({
        title:title.value,
        done:false
    })
    title.value=""
}

let active = computed(()=>{
    return todos.value.filter(v=>!v.done).length
})
let all = computed(()=>{
    return todos.value.length
})
let allDone = computed({
    get: function(){
        return active.value===0
    },
    set: function(val){
        todos.value.forEach(todo =>{
            todo.done=val
        })
    }
})
function clear(){
    todos.value = todos.value.filter(v=>!v.done)
}
</script>

<style >
.done{
    text-decoration: line-through;
    color: gray;
}
</style>