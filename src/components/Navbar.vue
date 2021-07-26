<template>
  <nav>
    <v-app-bar text app class="elevation-0">
        <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title class="text-uppercase grey--text">
            <span class="font-weight-light">Todo</span>
            <span>Ninja</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>

        <!-- dropdown Menu -->
        <v-menu offset-y> <!-- offset-y so button isn't covered -->
            <template v-slot:activator="{ on, attrs }">
                <v-btn text v-on="on" v-bind="attrs" color="grey">
                    <v-icon left>mdi-chevron-down</v-icon>
                    <span>Menu</span>
                </v-btn>
            </template>
            <v-list>
                <v-list-item v-for="link in links" v-bind:key="link.text" router v-bind:to="link.route">
                    <v-list-item-title>{{ link.text }}</v-list-item-title>
                </v-list-item>
            </v-list>
        </v-menu>
        
        <v-btn text color="grey">
            <span>Sign Out</span>
            <v-icon right>mdi-exit-to-app</v-icon>
        </v-btn>
    </v-app-bar>

    
    <v-navigation-drawer v-model="drawer" app class="primary">
       
        <v-row justify="center" class="mt-5">
            <v-col cols="6">
                <v-avatar size="100">
                    <img src="/avatar-1.png" alt="">
                </v-avatar>
                <p class="white--text subheading mt-1">The Net Ninja</p>
            </v-col>
        </v-row>

        <v-row justify="center" class="my-5">
            <Popup></Popup>
        </v-row>

        <v-list>
            <v-list-item v-for="link in links" v-bind:key="link.text" router v-bind:to="link.route">
                <v-list-item-action>
                    <v-icon class="white--text">{{link.icon}}</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title class="white--text">{{link.text}}</v-list-item-title>
                </v-list-item-content>
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import Popup from './Popup.vue'

export default {
    components: {
        Popup
    },

    data() {
        return {
            drawer: false,
            links:[
                { icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/' },
                { icon: 'mdi-folder', text: 'My Projects', route: '/projects' },
                { icon: 'mdi-account', text: 'Team', route: '/team' },
            ]
        }
    }
}
</script>

<style>

</style>