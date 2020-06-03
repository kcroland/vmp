<template>
  <v-app>
    <v-navigation-drawer app dark clipped src="../assets/drawback2.jpg">
      <!-- <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            VMP
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider class="mx-4"></v-divider> -->

      <v-list dense nav class="px-5 pt-5">
        <v-list-item
          v-slot:default="{ active }"
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
          class="my-2 py-1"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title class="subtitle-1">{{
              item.title
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <!-- Admin Pages -->
      <v-list-item class="mt-4">
        <v-list-item-content>
          <v-list-item-title class="title">
            Admin
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider class="mx-4"></v-divider>

      <v-list dense nav class="px-5">
        <v-list-item
          v-for="item in adminItems"
          :key="item.title"
          :to="item.to"
          link
          class="my-2 py-1"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title class="subtitle-1">
              {{ item.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app clipped-left dark class="primary">
      <v-img src="../assets/fodp-logo.png" max-width="300px" />

      <v-divider class="mx-4" inset vertical></v-divider>

      <v-toolbar-title class="pl-5 headline text-uppercase font-weight-bold" id="vmp">
        Vegetation Management Platform
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn fab small class="mr-3">
        <v-icon>mdi-cog</v-icon>
      </v-btn>
      <v-dialog v-model="dialog" persistent max-width="600px">
        <template v-slot:activator="{ on }">
          <v-btn fab small v-on="on">
            <v-icon>mdi-account</v-icon>
          </v-btn>
        </template>
        <v-card>
          <v-card-title>
            <span class="headline">User Login</span>
          </v-card-title>
          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12">
                  <v-text-field label="Email" required></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-text-field
                    label="Password"
                    type="password"
                    required
                  ></v-text-field>
                </v-col>
              </v-row>
            </v-container>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false"
              >Cancel</v-btn
            >
            <v-btn color="blue darken-1" text @click="dialog = false"
              >Login</v-btn
            >
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-app-bar>

    <!-- Sizes content based upon application components -->
    <v-content class="secondary">
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-content>

    <v-footer app class="primary">
      <v-spacer></v-spacer>
      <div>&copy; Kyle Roland | Nirmalya Ghosh | Eddie Yuen</div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "Index",
  data: () => ({
    items: [
      { icon: "mdi-home", title: "Dashboard Home", to: "/" },
      { icon: "mdi-map-marker", title: "Park Maps", to: "park-maps" },
      { icon: "mdi-table", title: "Data Tables", to: "tables" },
      { icon: "mdi-file-document", title: "Request Forms", to: "forms" }
    ],
    adminItems: [
      { icon: "mdi-chart-areaspline", title: "Forecasting", to: "" },
      { icon: "mdi-account-multiple", title: "User Management", to: "" },
      { icon: "mdi-database", title: "Edit Database", to: "" }
    ],
    dialog: false
  })
};
</script>

<style scoped>
  #vmp {
    color: #0000004a;
  }
</style>