<template>
  <div class="">
    <v-list
      class="pt-0"
      flat
    >
      <div
        v-for="task in tasks"
        :key= task.id
      >
        <v-list-item
          @click="doneTask(task.id)"
          :class="{ 'teal lighten-4' : task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through' : task.done }"
              >
                {{task.title}}
              </v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn 
                icon
                @click.stop="deleteTask(task.id)"
              >
                <v-icon color="red lighten-1">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>

  export default {
    name: 'Home',
    data() {
      return {
        tasks:[
          {
            id:1,
            title:'Wakey wakey',
            done:false,
          },
          {
            id:2,
            title:'Wash',
            done:false,
          },
          {
            id:3,
            title:'put sum cloths on',
            done:false,
          },
        ]
      }
    },
    methods: {
      doneTask(id) {
        let task = this.tasks.filter(task => task.id === id)[0]
        task.done = !task.done
      },
      deleteTask(id) {
        this.tasks = this.tasks.filter(task => task.id !== id)
      }
    }
  }
</script>
