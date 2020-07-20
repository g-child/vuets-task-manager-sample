<template>
  <v-container>
    <div>
      <v-data-table
        :headers="headers"
        :items="tasks"
        hide-default-footer
        hide-default-header
        sort-by.sync="isFinished"
        class="elevation-1"
      >
        <template v-slot:item.isFinished="{ item }">
          <v-simple-checkbox v-model="item.isFinished"></v-simple-checkbox>
        </template>
      </v-data-table>
    </div>
    <v-dialog v-model="dialog" width="800px">
      <template v-slot:activator="{ on }">
        <v-btn bottom color="pink" dark fab fixed right v-on="on">
          <v-icon>mdi-plus</v-icon>
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="grey darken-2">
          New Task
        </v-card-title>
        <v-container>
          <v-row no-gutters class="mx-3">
            <v-col cols="6">
              <v-text-field
                v-model="task.title"
                prepend-icon="mdi-pen"
                placeholder="Title"
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-text-field
                v-model="task.description"
                prepend-icon="mdi-text"
                placeholder="Description"
              ></v-text-field>
            </v-col>
          </v-row>
        </v-container>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn text color="primary" @click="dialog = false">Cancel</v-btn>
          <v-btn
            text
            @click="
              addTask();
              dialog = false;
            "
            >Save</v-btn
          >
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Tasks",
  data: () => ({
    dialog: false,
    headers: [
      {
        align: "start",
        sortable: false,
        value: "isFinished",
        width: "20"
      },
      { text: "Title", value: "title" },
      { text: "Description", value: "description" }
    ],
    tasks: [
      {
        title: "TODO の一覧表示",
        description: "Vuetify 使いました",
        isFinished: true
      },
      {
        title: "Azure へのデプロイ",
        description: "デプロイ先は Azure Static WebApps を利用",
        isFinished: true
      },
      {
        title: "TODO の追加",
        description: "",
        isFinished: true
      },
      {
        title: "TODO の完了",
        description: "",
        isFinished: true
      },
      {
        title: "TODO の削除",
        description: "",
        isFinished: false
      }
    ],
    task: {
      title: "",
      description: "",
      isFinished: false
    }
  }),
  methods: {
    addTask: function() {
      this.tasks.push({ title: "add", description: "", isFinished: false });
    }
  }
});
</script>
