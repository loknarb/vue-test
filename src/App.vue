<template>
  <v-app id="inspire">
    <v-app-bar app color="white" flat>
      <v-container class="py-0 fill-height">
        <v-avatar class="mr-10" color="grey darken-1" size="32"></v-avatar>

        <v-btn v-for="link in links" :key="link" text>
          {{ link }}
        </v-btn>
        <v-btn v-if="shouldShowDOMElement" @click="shouldShowDOMElement = false" text
          >Hide List</v-btn
        >
        <v-btn v-else @click="shouldShowDOMElement = true" text>Show List</v-btn>
        <v-spacer></v-spacer>

        <v-responsive max-width="260">
          <!-- <v-text-field
            dense
            flat
            hide-details
            rounded
            solo-inverted
          ></v-text-field> -->
        </v-responsive>
      </v-container>
    </v-app-bar>
    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col cols="2">
            <v-sheet rounded="lg">
              <v-list color="transparent">
                <v-list-item v-for="n in 5" :key="n" link>
                  <v-list-item-content>
                    <v-list-item-title> List Item {{ n }} </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>

                <v-divider class="my-2"></v-divider>

                <div v-if="shouldShowDOMElement">
                  <v-list-item
                    v-for="({ message }, index) in items"
                    :key="index"
                    link
                    color="grey lighten-4"
                  >
                    <v-list-item-content>
                      <v-list-item-title> {{ message }} </v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                  <v-list-item color="lighten-4 grey" link>
                    <v-list-item-content>
                      <v-list-item-title> Refresh </v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </div>
              </v-list>
            </v-sheet>
          </v-col>

          <v-col>
            <v-sheet min-height="70vh" rounded="lg"> </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
export default {
  data: () => ({
    greeting: 'Hello Vue!',
    links: ['Dashboard', 'Messages', 'Profile', 'Updates'],
    items: [{ message: 'Hello' }, { message: 'World' }, { message: '!' }],
    shouldShowDOMElement: true,
  }),
};
</script>
