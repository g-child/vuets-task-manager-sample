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
  </v-container>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "HelloWorld",

  data: () => ({
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
        isFinished: false
      },
      {
        title: "TODO の完了",
        description: "",
        isFinished: false
      },
      {
        title: "TODO の削除",
        description: "",
        isFinished: false
      }
    ]
  })
});
</script>
