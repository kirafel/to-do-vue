<template>
  <div>
       <form class="row justify-content-center mt-5 w-100" @submit.prevent="addTodo">
           <input v-model="title" type="text" name="title" id="title" class="form-control mr-2 col-3" placeholder="Todo Item" />
           <button :disabled="title === ''" type="submit" class="btn btn-outline-info">Add Todo</button>
        </form>
  </div>
</template>

<script>
export default {
    name : 'AddToDo',
    data() {
        return {
            title : ''
        }
    },  
    methods : {
        addTodo: function() {
            this.$emit('addTodo', this.title);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    input {
        outline: none !important;
        box-shadow: none !important;
    }
</style>