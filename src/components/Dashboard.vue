<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>

    <v-container class="my-5">

      <v-row class="mb-3">
        <v-col md="2" sm="4" xs="2" lg="2">
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn small text color="grey" v-on:click="sortBy('title')" v-bind="attrs" v-on="on">
                <v-icon left small>mdi-folder</v-icon>
                <span class="caption text-lowercase">By Project name</span>
              </v-btn>
            </template>
            <span>Sort projects by title</span>
          </v-tooltip>
        </v-col>

        <v-col md="2"  sm="4" xs="2" lg="2">
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn small text color="grey" v-on:click="sortBy('person')" v-bind="attrs" v-on="on">
                <v-icon left small>mdi-account</v-icon>
                <span class="caption text-lowercase">By Person</span>
              </v-btn>
            </template>
            <span>Sort projects by person</span>
          </v-tooltip>
        </v-col>
      </v-row>

      <v-card
        flat
        tile
        class="px-3 my-4"
        v-for="project in projects"
        v-bind:key="project.title"
        color="grey lighten-3"
      >
        <v-row row wrap>
          <v-col cols="12" md="6" v-bind:class="`pl-3 project ${project.status}`">
            <div class="caption grey--text">Project Title</div>
            <div>{{ project.title }}</div>
          </v-col>
          <v-col xs="2">
            <div class="caption grey--text">Person</div>
            <div>{{ project.person }}</div>
          </v-col>
          <v-col xs="2">
            <div class="caption grey--text">Due Date</div>
            <div>{{ project.due }}</div>
          </v-col>
          <v-col xs="2">
            <div class="float-right mx-5">
              <v-chip v-bind:class="`${project.status} white--text caption my-2`">{{project.status}}</v-chip>
            </div>
          </v-col>
        </v-row>
        <v-row cols="12">
          <v-divider></v-divider>
        </v-row>
      </v-card>

    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          title: "Design a new website",
          person: "Domga",
          due: "1st Jan 2019",
          status: "ongoing",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
        },
        {
          title: "Code up the homepage",
          person: "Chun Li",
          due: "10th Jan 2019",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
        },
        {
          title: "Design video thumbnails",
          person: "Ryu",
          due: "20th Dec 2018",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
        },
        {
          title: "Create a community forum",
          person: "Gouken",
          due: "20th Oct 2018",
          status: "overdue",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!",
        },
      ],
    };
  },

  methods: {
    sortBy (param){
      this.projects.sort((a, b) => a[param] < b[param] ? -1 : 1) // 1 if order is to change, -1 if order is correct
    }
  }
};
</script>

<style scoped>
.project.complete {
  border-left: 4px solid #3cd1c2;
}
.project.ongoing {
  border-left: 4px solid orange;
}
.project.overdue {
  border-left: 4px solid tomato;
}

.v-chip.ongoing {
    background: #fed330 !important;
  }
  .v-chip.complete {
    background: #26de81 !important;
  }
  .v-chip.overdue {
    background: #fc5c65 !important;
  }
</style>