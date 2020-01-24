<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
    >
      <v-list dense>
        <template v-for="item in items">
          <v-list-item
            :key="item.text"
            :to="item.text"
            link
          >
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title
        style="width: 300px"
        class="ml-0 pl-4"
      >
        <span class="hidden-sm-and-down">Dashboard</span>
      </v-toolbar-title>
      <v-text-field
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="mdi-magnify"
        label="Search"
        class="hidden-sm-and-down"
      />
      <v-spacer />
      <v-btn icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
      <v-btn icon>
        <v-badge
          color="blue"
          content="6"
          offset-x="8"
          offset-y="8"
        >
          <v-icon>mdi-bell</v-icon>
        </v-badge>
      </v-btn>
    </v-app-bar>

    <v-content>
      <router-view/>
    </v-content>

    <v-footer
      app
    >
      <span class="white--text">
        &copy; 2020 Copyright: <a href="https://traveler0401.com/" target="_blank">Traveler</a>
      </span>
    </v-footer>

    <v-btn
      bottom
      color="blue"
      fab
      fixed
      right
      @click="dialog = !dialog"
    >
      <v-icon>mdi-plus</v-icon>
    </v-btn>

    <v-dialog
      v-model="dialog"
      width="800px"
    >
      <v-card>
        <v-card-title class="grey darken-2">
          Create contact
        </v-card-title>
        <v-container>
          <v-row class="mx-2">
            <v-col
              class="align-center justify-space-between"
              cols="12"
            >
              <v-row
                align="center"
                class="mr-0"
              >
                <v-avatar
                  size="40px"
                  class="mx-3"
                >
                  <img
                    src="//ssl.gstatic.com/s2/oz/images/sge/grey_silhouette.png"
                    alt=""
                  >
                </v-avatar>
                <v-text-field
                  placeholder="Name"
                />
              </v-row>
            </v-col>
            <v-col cols="6">
              <v-text-field
                prepend-icon="mdi-account-card-details-outline"
                placeholder="Company"
              />
            </v-col>
            <v-col cols="6">
              <v-text-field
                placeholder="Job title"
              />
            </v-col>
            <v-col cols="12">
              <v-text-field
                prepend-icon="mdi-mail"
                placeholder="Email"
              />
            </v-col>
            <v-col cols="12">
              <v-text-field
                type="tel"
                prepend-icon="mdi-phone"
                placeholder="(000) 000 - 0000"
              />
            </v-col>
            <v-col cols="12">
              <v-text-field
                prepend-icon="mdi-text"
                placeholder="Notes"
              />
            </v-col>
          </v-row>
        </v-container>
        <v-card-actions>
          <v-spacer />
          <v-btn
            text
            color="primary"
            @click="dialog = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            @click="dialog = false"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'App',
  data: () => ({
    dialog: false,
    drawer: null,
    items: [
      { icon: 'mdi-home',           text: 'Home' },
      { icon: 'mdi-message',        text: 'Send feedback' },
      { icon: 'mdi-cellphone-link', text: 'App downloads' },
      { icon: 'mdi-keyboard',       text: 'Go to the old version' },
      { icon: 'mdi-settings',       text: 'Settings' },
      { icon: 'mdi-help-circle',    text: 'Help' },
    ],
  }),
});
</script>
