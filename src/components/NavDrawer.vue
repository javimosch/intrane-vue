<template>
  <v-layout full-height>
    <!-- <v-system-bar color="deep-purple darken-3"></v-system-bar> -->

    <v-app-bar color="primary" prominent>
      <v-app-bar-nav-icon
        icon="mdi-integrated-circuit-chip"
        variant="text"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>

      <v-toolbar-title>Geored Admin</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn variant="text" icon="mdi-magnify"></v-btn>

      <v-btn
        @click.stop="rightDrawer = !rightDrawer"
        variant="text"
        icon="mdi-dots-vertical"
      ></v-btn>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" location="left" temporary>
      <v-list :items="items">
        <template #item="{ title, value }">
          <div>
            <v-btn :prepend-icon="value?.icon||'mdi-cancel'" variant="text" block size="large" class="my-3">
              {{ title }}
            </v-btn>
          </div>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-navigation-drawer v-model="rightDrawer" location="right" temporary>
      <div flex flex-col items-center justify-end style="height:inherit">
        <!-- Bottom -->
        <div flex flex-col items-center justify-center>
          <div background="green-200 red" style="height:2px;width:15rem"  class="bg-red-darken-3"></div>
          <div mx-2 my-2>
            <div flex flex-col items-center justify-center p-2>
              <div>
                <v-icon color="grey" size="70" icon="mdi-account-circle"></v-icon>
              </div>

              <p mt-2 text-6>Javi</p>
            </div>
          </div>
          <v-btn prepend-icon="mdi-logout" variant="text" block size="large" class="my-3">
            Logout
          </v-btn>
        </div>
      </div>
    </v-navigation-drawer>

    <v-main h-screen>
      <slot></slot>
    </v-main>
  </v-layout>
</template>
<script lang="ts">
export default {
  data: () => ({
    rightDrawer: false,
    drawer: false,
    group: null,
    items: [
      {
        title: 'Users',
        value: {
          icon: "mdi-account"
        },
        
      },
      {
        title: 'Bar',
        value: 'bar'
      },
      {
        title: 'Fizz',
        value: 'fizz'
      },
      {
        title: 'Buzz',
        value: 'buzz'
      }
    ]
  }),

  watch: {
    group() {
      this.drawer = false
    }
  }
}
</script>
