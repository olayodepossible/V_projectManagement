<template>

<v-dialog width="600">
      <template v-slot:activator="{ on, attrs }">
        <v-btn text class="success" v-bind="attrs" v-on="on">
          Add New Project
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="headline grey lighten-2">
          <h5>Add a New Project</h5>
        </v-card-title>

        <v-card-text>
            <v-form class="px-3">
                <v-text-field label="Title" v-model="title" prepend-icon="mdi-folder"></v-text-field>
                <v-textarea label="Information" v-model="content" prepend-icon="mdi-pencil"></v-textarea>

                <v-menu>
                     <template v-slot:activator="{ on, attrs }">
                         <v-text-field :value= "formattedDate"  v-bind="attrs" v-on="on" label="Due Date" prepend-icon="mdi-calendar"></v-text-field>
                    </template>
                    <v-date-picker v-model= "due" ></v-date-picker>
                </v-menu>
            </v-form>
        </v-card-text>

        <!-- <v-divider></v-divider> -->

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="success"
            depressed
            @click="submit "
          >
            Add Project
          </v-btn>
        </v-card-actions>

      </v-card>
    </v-dialog>

</template>

<script>
import moment from 'moment'
export default {
    data(){
        return {
            title: "",
            due: null,
            content: ""
        }
    },
    methods: {
        submit(){
            console.log(this.title, this.content);
            this.title ="";
            this.content ="";
            this.due = null
        }
    },
    computed:{
        formattedDate() {
            return this.due ? moment(this.due).format("Do MMM YYYY") : '' 
        }
    },
    filters: {
    moment: function (date) {
      return moment(date).format('MMMM Do YYYY, h:mm:ss a');
    }
  }
}
</script>