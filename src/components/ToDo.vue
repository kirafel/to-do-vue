<template>
    <div class="container mt-4">
        <div class="list-group mt-5">
            <div class="list-group-item text-left" :key="todo.id" v-for="todo in todos">
                <input type="checkbox" class="mx-3" :checked="todo.completed" @change="toggle(todo)">
                <!-- Method 1 -->
                <span :class="{'is-completed' : todo.completed}">
                    {{ todo.title}}
                </span>

                <!-- Method 2 -->
                <!-- <del v-if="todo.completed">
                    {{ todo.title}}
                </del>
               <span v-else>
                    {{ todo.title}}
               </span> -->

                <!-- Method 3 -->
                <!-- <del v-show="todo.completed">
                    {{ todo.title}}
                </del>
               <span v-show="!todo.completed">
                    {{ todo.title}}
               </span> -->

               <button @click="$emit('delete-item', todo.id)" class="badge badge-danger float-right">X</button>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    name : 'ToDo',
    props : {
        todos : Array,
    },
    methods: {
        toggle: function(todo) {
            todo.completed = !todo.completed;
        },
    }
}
</script>

<style>
.is-completed {
    text-decoration: line-through;
}
</style>