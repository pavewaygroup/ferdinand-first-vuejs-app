<template>
  <v-container>
    <v-layout row>
      <v-flex xs12 sm4 offset-sm4>
        <v-card>
          <v-toolbar color="teal" dark>

            <v-toolbar-title class="text-xs-center">Todo List App</v-toolbar-title>

            <v-spacer></v-spacer>

            <v-btn icon @click="state=true">
              <v-icon>add</v-icon>
            </v-btn>
          </v-toolbar>

          <v-container v-if="state">
            <v-layout row wrap>
              <v-flex xs12>
                <v-text-field
                  name="name"
                  label="Add item"
                  id="item"
                  hint="write thing to do"
                  v-model="item"
                  @keyup.enter="addItem"
                ></v-text-field>
              </v-flex>
            </v-layout>
          </v-container>

          <v-list subheader>
            <v-subheader>Things to do</v-subheader>
            <v-list-tile
              v-for="(item, index) in items"
              :key="index"
              @click=""
            >
              <v-list-tile-action>
                <v-checkbox @click="checkedItem(index)"></v-checkbox>
              </v-list-tile-action>

              <v-list-tile-content>
                <v-list-tile-title v-text="item"></v-list-tile-title>
              </v-list-tile-content>

              <v-list-tile-action>
                <v-icon @click="removeItem(index)">delete</v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list>

          <v-divider></v-divider>

          <v-list subheader>
            <v-subheader>Done</v-subheader>

            <v-list-tile
              v-for="(item,index) in items1"
              :key="index"
            >
              <v-list-tile-action>
                <v-checkbox @click=""></v-checkbox>
              </v-list-tile-action>

              <v-list-tile-content>
                <v-list-tile-title v-text="item"></v-list-tile-title>
              </v-list-tile-content>

              <v-list-tile-action>
                <v-icon @click="removeItem(index)">delete</v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    data () {
      return {
        item: null,
        state:false,
        items: [],
        items1: []
      }
    },
    methods:{
      addItem(){
        this.items.push(this.item)
        this.item=null
      },
      removeItem(index){
        this.items.splice(index,1)
      },
      checkedItem(index){
        this.items1.push(this.items)
        this.items.splice(index,1)
      }
    }
  };
</script>