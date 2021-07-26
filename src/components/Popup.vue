<template>
   <div class="text-center">
       
    <v-dialog width="500">
      <template v-slot:activator="{ on }">
        <v-btn class="success" dark v-on="on">Add New Project</v-btn>
      </template>
      <v-card>
        <v-card-title class="headline grey lighten-2" primary-title>Add a New Project</v-card-title>
        <v-card-text>
            <v-form class="px-3" ref="form">
                <v-text-field prepend-icon="mdi-folder" label="Title" v-model="title" v-bind:rules="inputRules"></v-text-field>
                <v-textarea prepend-icon="mdi-pencil" label="Information" v-model="information" v-bind:rules="inputRules"></v-textarea>


                <!-- DatePicker -->
                <v-menu max-width="290">
                    <template v-slot:activator="{ on }">
                        <v-text-field v-bind:value="due" label="Due date" prepend-icon="mdi-calendar-range" v-on="on" v-bind:rules="inputRules"></v-text-field>
                    </template>
                    <v-date-picker v-model="due"></v-date-picker>
                </v-menu>
                                

                <v-btn class="success mx-0" justify="center" v-on:click="submit">Add Project</v-btn>           
            </v-form>
        </v-card-text>
      </v-card>
    </v-dialog>

  </div>
</template>

<script>
export default {
    data () {
        return {
            title: '',
            information: '',
            due: null,
            inputRules: [
               v =>  v && v.length >= 3 || 'Minimum length is 3 characters'
            ]
        }
    },

    methods: {
        submit() {
            if(this.$refs.form.validate()){
                console.log(this.title);
                console.log(this.information);
            }
        }
    }
}
</script>

<style>

</style>