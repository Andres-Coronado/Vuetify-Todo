<template>

  <v-list flat class="pt-1">
        <v-text-field
          v-model="newTaskTitle"
          @click:append="addTask"
          @keyup.enter="addTask"
          class="pa-3"
          outlined
          label="Add Task"
          append-icon="add"
          hide-details
          clearable
        >

        </v-text-field>

    <div v-for="task in tasks" :key="task.id">
      <v-list-item
        @click="doneTask(task.id)"
        :class="{ 'blue lighten-5': task.done }"
      >
        <template v-slot:default>
          <v-list-item-action>
            <v-checkbox :input-value="task.done"></v-checkbox>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title
              :class="{ 'text-decoration-line-through': task.done }"
            >
              {{ task.title }}
            </v-list-item-title>
          </v-list-item-content>

          <v-list-item-action>
            <v-btn icon @click.stop="deleteTask(task.id)">
              <v-icon color="red lighten-1">delete</v-icon>
            </v-btn>
          </v-list-item-action>
        </template>
      </v-list-item>
      <v-divider></v-divider>
    </div>
  </v-list>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  data() {
    return {
      newTaskTitle:'',
      tasks: [
        // {
        //   id: 1,
        //   title: "Hola",
        //   done: false,
        // },
        // {
        //   id: 2,
        //   title: "doritos",
        //   done: true,
        // },
        // {
        //   id: 3,
        //   title: "Epura",
        //   done: false,
        // },
      ],
    };
  },
  methods: {
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false
      }
      this.tasks.push(newTask)
      this.newTaskTitle = '';
    },
    doneTask(id) {
      let task = this.tasks.filter((task) => task.id === id)[0];
      task.done = !task.done;
      console.log(task.done);
    },
    deleteTask(id) {
      console.log(id);
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>
