<template>
  <div class="dashboard">
       <h1 class="subheading grey--text">Dashboard</h1>

    <v-container class="my-5">
      <v-row class="mb-3">
        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
              <v-btn small  depressed color="grey lighten-3 mr-3" @click="sortBy('title')"  v-bind="attrs" v-on="on">
                <v-icon left>mdi-folder</v-icon>
                <span class="caption text-lowercase">By Project</span>
              </v-btn>
           </template>
          <span>Sort by Project</span>
        </v-tooltip>

        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
              <v-btn small  depressed class="grey lighten-3"  @click="sortBy('person')" v-bind="attrs" v-on="on">
                <v-icon left>mdi-account</v-icon>
                <span class="caption text-lowercase">By Person</span>
              </v-btn>
           </template>
            <span>Sort by Person</span>
        </v-tooltip>


        <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
                 
            color="primary"
            dark
            v-bind="attrs"
            v-on="on"
          >
            Button
          </v-btn>
          <v-icon
            color="primary"
            dark
            v-bind="attrs"
            v-on="on"
          >
            mdi-home
          </v-icon>
        </template>
        <span>Tooltip</span>
      </v-tooltip>
      </v-row>

      <v-card flat >
        <v-row wrap>
          <v-col class="caption grey--text"  cols="12" sm="4" md="2">Project Title</v-col>
          <v-col class="caption grey--text" cols="12" sm="4" md="2">Person</v-col>
          <v-col class="caption grey--text" cols="12" sm="4" md="2">Due Date</v-col>
          <v-col class="caption grey--text" cols="12" sm="4" md="2">Status</v-col>
        </v-row>
       

        <v-row wrap  class="mb-4" v-for="project in projects" :key="project.title" :class="`pa-3 project ${project.status}`">
          <v-col class="caption grey--text" cols="12" sm="4" md="2"> {{project.title}}</v-col>
          <v-col class="caption grey--text"  cols="12" sm="4" md="2">{{project.person}}</v-col>
          <v-col class="caption grey--text" cols="12" sm="4" md="2"> {{project.due}}</v-col>
          <v-col class="caption grey--text" cols="12" sm="4" md="2">
            <div class="right">
              <v-chip small class="caption white--text my-2" :class=" ` ${project.status}` "> {{project.status}}</v-chip>
            </div>
            
          </v-col>
        </v-row>

      </v-card>
      
      <v-layout wrap align-center>
        <v-flex xs12 sm6 d-flex>
             <v-select
                  v-model="selectedBank"
                  :items="items"
                  item-text="bankName"
                  label="Select a bank"
                  persistent-hint
                  return-object
                  single-line
                ></v-select>
        </v-flex>
            <v-btn rounded block color="blue darken-3" dark large @click="directToBank()">CONTINUE</v-btn>
      </v-layout>
    </v-container>
  </div>
</template>


<script>
export default {
  data() {
    return {
      projects: [
        { title: 'Design a new website', person: 'The Net Ninja', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Code up the homepage', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Design video thumbnails', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Create a community forum', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
      ],

      items: [
      {value: '1', bankName: 'Bank1'},
      {value: '2', bankName: 'Bank2'},
    ],
    selectedBank: null
    }
  },

  methods:{
    sortBy(value){
      this.projects.sort((a, b) => a[value] < b[value] ? -1 : 1)
    },

    directToBank() {
        alert('Label: ' + this.selectedBank.bankName + '; Value: ' + this.selectedBank.value)
        console.log("Label: ", this.selectedBank.bankName)
        console.log("Value: ", this.selectedBank.value)
    }
  
  }
}
</script>

<style scoped>
.project.complete{
  border-left: 4px solid #3cd1c2;
}
.project.ongoing{
  border-left: 4px solid orange;
}
.project.overdue{
  border-left: 4px solid rgb(63, 62, 62);
}

.v-chip.complete{
  background-color: #3cd1c2!important;
}
.v-chip.ongoing{
  background-color: #ffaa2c!important;
}
.v-chip.overdue{
  background-color: #f83e70 !important;
 color: #47e0a9;
}
</style>
