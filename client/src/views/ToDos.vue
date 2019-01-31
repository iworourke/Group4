<template>
     <div>
        <div class="todos">

            <div> Todos </div>

            <ul>
                <li v-for="(todo, index) in mytodos" v-bind:key="index" > {{todo.name}} </li>
            </ul>
        
            <div class="buttons">
                <a class="button is-primary" v-on:click="showAddTodoModal()">
                <strong>New Item</strong>
                </a>
            </div>

        </div>

        <Modal v-bind:is-showing="showAddTodo" title="AddTodo" v-on:success="successAddTodo()" v-on:cancel="cancelAddTodo()">
            <AddTodo/>
        </Modal>
    </div>
</template>

<script lang="ts">

import Vue from 'vue'
import { Component } from "vue-property-decorator";
import Modal from "@/components/Modal.vue";
import AddTodo from "@/components/AddTodo.vue";

@Component({
    components: {
        Modal,
        AddTodo
    }
})
export default class ToDos extends Vue {
    
    public showAddTodo: boolean = false;
    
    mytodos: ToDo[] = [
        { name : "Tod one", duedate : undefined },
        { name : "Tod two", duedate : undefined }
    ];

    showAddTodoModal() {
        this.showAddTodo = true;
    }
    successAddTodo() {
        this.mytodos.push({name: `todo${new Date().getTime()}` , duedate: undefined});
        this.showAddTodo = false;
    }
    cancelAddTodo() {
        this.showAddTodo = false;
    }
    addTodItem() {
        this.mytodos.push({name: `todo${new Date().getTime()}` , duedate: undefined});
    }

}

interface ToDo {
    name: string;
    duedate: Date | undefined;
}

</script>