<template>
  <v-app>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon />
      <v-icon class="mx-4" large> mdi-video </v-icon>
      <v-toolbar-title>
        <span class="title">VideoVue</span>
      </v-toolbar-title>
      <v-spacer />
      <v-text-field
        solo
        placeholder="Search..."
        single-line
        append-icon="mdi-magnify"
        color="white"
        class="mt-6"
      ></v-text-field>
      <v-spacer />
      <v-btn class="ml-0" icon>
        <v-icon> mdi-apps</v-icon>
      </v-btn>
      <v-btn class="ma-2" icon>
        <v-icon> mdi-bell</v-icon>
      </v-btn>
      <div>
        <v-menu
          v-model="menu"
          :close-on-content-click="false"
          :nudge-witdh="250"
          offset-x
        >
          <template v-slot:activator="{ on }">
            <v-avatar size="40">
              <img
                v-on="on"
                src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80"
              />
            </v-avatar>
          </template>
          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title> Fouzia BENADIDA </v-list-item-title>
                  <v-list-item-substile> VideoVue </v-list-item-substile>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider />
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-action>
                <v-list-item-title> Settings </v-list-item-title>
              </v-list-item>
            </v-list>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-switch v-model="theme" color="purple"></v-switch>
                </v-list-item-action>
                <v-list-item-title> Dark theme </v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer />
              <v-btn color="primary" text @click="menu = false">
                Çikiş Yap
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <v-content>
      <v-container>
        <v-row class="mb-4">
          <v-col sm="6" md="4" lg="3" v-for="(item, index) in 200" :key="index">
            <v-card>
              <v-img
                height="200px"
                :src="`https://picsum.photos/500/300?image=${index + 1}`"
                :lazy-src="`https://picsum.photos/500/300?image=${index + 1}`"
              />
              <v-card-substile class=""> Number {{ item }} </v-card-substile>
              <v-card-text class="text--primary"
                ><div>Header field</div>
                <div>Header Content</div></v-card-text
              >
              <v-card-actions>
                <v-btn color="orange" text> Save </v-btn>
                <v-btn color="orange" text> Share </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    menu: false,
    theme: false,
  }),
  watch: {
    theme: function (next) {
      this.$vuetify.theme.dark = next;
    },
  },
};
</script>
