<template>
  <form  v-on:submit.prevent="onSubmit">
    <div class="field">
      <label class="label">Task Name</label>
      <div class="control">
        <input class="input" type="text" placeholder="task name" v-bind="addtodo.taskName"/>
      </div>
    </div>
    <div class="field">
      <label class="label">Task Status</label>
      <div class="control">
        <input class="input" type="text" placeholder="task status" v-bind="addtodo.taskStatus"/>
      </div>
    </div>
  </form>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class AddTodo extends Vue {
  addtodo: AddTodoForm = {
    taskName: "",
    taskStatus: ""
  };
}

export interface AddTodoForm {
  taskName: string;
  taskStatus: string;
}
</script>
