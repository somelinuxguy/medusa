<template>
    <form @submit.prevent="onSubmit">
        <label class="bugs" for="new-todo-input">
        What needs doin?
        </label><br>
        <input
            type="text"
            id="new-todo-input"
            name="new-todo"
            autocomplete="off"
            v-model.lazy.trim="label"
        />
        <button type="submit">
            Add
        </button>
    </form>    
</template>

<script>
    export default {
        data() {
            return {
                label: ""
            }
        },
        methods: {
            onSubmit(){
                if(this.label === "") {
                    console.log("Refusing to add empty items to the list.");
                    return;
                }
                console.log('Todoform component: ', this.label);
                this.$emit('todo-added', this.label);
                this.label = "";
            }
        }
    };

</script>
// style scoped to this component.
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.bugs {
    color: red;
    font-weight: bold;
}
</style>
