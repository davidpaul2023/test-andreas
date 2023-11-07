<template>
    <v-app>
        <div class="bg-teal-lighten-1 h-100 d-flex justify-center align-center flex-column">
            <h1 class="text-h2 font-weight-bold pa-4">Vue ToDO List</h1>
            <div class=" bg-white mb-6">
                <v-card style="width: 700px;" rounded="50%">
                    <v-card-item class="pa-0">
                        <v-card-actions class="d-flex justify-end gap-2 bg-grey-lighten-3 pa-5">
                            <v-chip
                            class="d-flex mr-2"
                            rounded="full"
                            variant="elevated"
                            color="blue"
                            :ripple="false" 
                            >
                            Tasks
                                <v-badge
                                class="ml-4 mr-2 mb-1"
                                color="white"
                                text-color="blue"
                                :content="taskList.length"
                                overlap
                                size="x-large"
                                ></v-badge>
                            </v-chip>
                            <v-chip
                            class="d-flex mr-2"
                            rounded="full"
                            variant="elevated"
                            color="blue"
                            :ripple="false" 
                            >
                            Tasks Done
                                <v-badge
                                class="ml-4 mr-2 mb-1"
                                color="white"
                                text-color="blue"
                                :content="doneTask.length"
                                size="x-large"
                                ></v-badge>
                            </v-chip>

                            <v-btn prepend-icon="mdi-trash-can" class="bg-red">
                                Done Tasks
                            </v-btn>
                            <v-btn prepend-icon="mdi-trash-can" class="bg-red">
                                Tasks
                            </v-btn>
                        </v-card-actions>


                        <v-card-title class="d-flex flex-column justify-start pa-5">
                            <v-btn 
                            density="compact"
                            class="w-100 bg-lighten-5 text-left task-button my-1"
                            prepend-icon="mdi-check-circle"
                            @click="doneTask(task.id)"
                            v-bind:key="task.id"
                            v-for="(task) in taskList"
                            >
                          {{ task.task }}
                            </v-btn>
                        </v-card-title>

                        <v-card-text class="bg-grey-lighten-3 pa-5">
                           <v-text-field
                                v-model="inputTask"
                                variant="outlined"
                                :loading="loading"
                                density="compact"
                                label="New Task"
                                class="rounded"
                                append-inner-icon="mdi-plus-circle-outline"
                                @click:append-inner="newTask"
                                rounded
                                color="blue"
                            ></v-text-field>
                        </v-card-text>
                    </v-card-item>
                </v-card>
            </div>
        </div>
    </v-app>
  </template>


<style scoped>
    .hidden-sm-and-down .v-icon {
    color: rgb(95, 20, 20) !important;
}   
.task-button {
  min-height: 52px;
  height: 100% !important;
  font-size: 14px;
  text-transform: none;
  justify-content: start;
}
</style>

<script>

  export default {
    name: 'Index',
    data: () => ({
      inputTask: '',
      loaded: false,
      loading: false,
      taskList: [],
      taskDone: [],
      idIncrement: 0,
    }),
    methods: {
      onClick () {
        this.loading = true

        setTimeout(() => {
          this.loading = false
          this.loaded = true
        }, 2000)
      },

      // add new teask
      newTask () {
         let task = {
          id: this.idIncrement,
          done: false,
          task: this.inputTask
         }
          this.taskList.push(task);
          this.idIncrement += 1;
          this.inputTask = '';

          console.log(this.taskList)
      },

      // task done
      doneTask(id) {
        this.taskList.id 
      },
    },
  }


  
</script>