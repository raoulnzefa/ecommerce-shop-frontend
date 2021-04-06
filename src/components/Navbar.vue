<template>
  <div id="navbar">
      <nav>
          <v-navigation-drawer
            v-model="drawer"
            app
            dark
            :mini-variant.sync="mini"
            class="red"
            >
                <v-list-item class="px-2">
                    <v-list-item-avatar>
                        <v-icon>mdi-basket-outline</v-icon>
                    </v-list-item-avatar>

                    <v-list-item-title class="text-uppercase">
                        <span class="font-weight-light">shop</span>
                        <span class="font-weight-bold">ify</span>    
                    </v-list-item-title>

                    <v-btn
                    icon
                    @click.stop="mini = !mini"
                    >
                    <v-icon>mdi-chevron-left</v-icon>
                    </v-btn>
                </v-list-item>

                <v-list>
                    <v-list-item-group v-model="model">
                        <v-list-item>
                            <v-list-item-icon>
                                <v-icon>mdi-view-dashboard</v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title>Home</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>

                        <v-list-item>
                            <v-list-item-icon>
                                <v-icon>mdi-percent</v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title>Sale</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>

                        <v-list-item>
                            <v-list-item-icon>
                                <v-icon>mdi-cart</v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title>My cart</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>

                        <v-list-item>
                            <v-list-item-icon>
                                <v-icon>mdi-cog</v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title>Settings</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                        
                    </v-list-item-group>
                    </v-list>
                
            </v-navigation-drawer>

            <v-app-bar app>
            <v-app-bar-nav-icon @click="drawer = !drawer" color="red"></v-app-bar-nav-icon>

                <v-toolbar-title
                class="text-uppercase red--text">
                    <span class="font-weight-light">shop</span>
                    <span class="font-weight-bold">ify</span>
                </v-toolbar-title>
            </v-app-bar>
      </nav>
  </div>
</template>

<script>
export default {
    data(){
        return {
            drawer: true,
            mini: true,
        }
    }
}
</script>

<style>

</style>