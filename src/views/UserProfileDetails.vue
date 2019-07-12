<template>
  <v-container>
    <v-layout
      justify-center
      row
      wrap>
      <v-flex
        xs12
        md8>
        <v-card>
          <v-layout>
            <v-flex xs5>
              <img
                src="https://randomuser.me/api/portraits/men/85.jpg"
                height="200px">
            </v-flex>

            <v-flex xs7>
              <v-card-title>
                <div>
                  <div class="headline">
                    John Leider
                  </div>

                  <div>
                    To view more details about John Leider.
                  </div>

                  <div>
                    Please click on the button below.
                  </div>
                </div>
              </v-card-title>

              <v-card-actions>
                <v-btn
                  color="blue"
                  dark
                  @click.stop = "drawer = !drawer">
                  View Details
                </v-btn>
              </v-card-actions>
            </v-flex>
          </v-layout>
        </v-card>

        <v-navigation-drawer
          v-model="drawer"
          app
          temporary
          right>
          <v-img
            :gradient="sidebarOverlayGradiant"
            src="/img/drawer_background2.jpg"
            height="100%">
            <v-container>
              <v-layout
                align-center
                justify-center
                column>
                <v-list>
                  <v-list-tile avatar>
                    <v-list-tile-avatar
                      class="mx-auto d-block"
                      size="120">
                      <div
                        v-viewer="{movable: false}"
                        class="images">
                        <img
                          v-for="src in images"
                          :src="src"
                          :key="src"
                          @click="show">
                      </div>
                    </v-list-tile-avatar>
                  </v-list-tile>
                </v-list>
                <v-list>
                  <v-lsit-tile
                    v-for="(user, i) in users"
                    :key="i">
                    <v-list-tile-content>
                      <v-list-tile-title>
                        <h4
                          class="name white--text font-weight-light mb-0">
                          {{ user.Name }}
                          <v-tooltip top>
                            <template v-slot:activator="{ on }">
                              <v-icon
                                color="white"
                                v-on="on">
                                mdi-human-male
                              </v-icon>
                            </template>
                            <span>
                              Single
                            </span>
                          </v-tooltip>
                        </h4>
                      </v-list-tile-title>
                    </v-list-tile-content>
                  </v-lsit-tile>
                  <v-lsit-tile
                    v-for="(user, i) in users"
                    :key="i">
                    <v-list-tile-content>
                      <v-list-tile-title>
                        <h6 class="white--text font-weight-thin mt-0 ">
                          {{ user.POB }}
                        </h6>
                      </v-list-tile-title>
                    </v-list-tile-content>
                  </v-lsit-tile>
                </v-list>
              </v-layout>
              <v-divider
                color="white"/>
            </v-container>
          </v-img>
        </v-navigation-drawer>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<style>
</style>

<script>
import 'viewerjs/dist/viewer.css'
import Viewer from 'v-viewer'
import Vue from 'vue'
Vue.use(Viewer, { name: 'viewer' })
export default {
  data: () => ({
    drawer: null,
    users: [
      {
        Name: 'John Leider',
        POB: 'Fort Worth, Texas'
      }
    ],
    images: [
      'https://randomuser.me/api/portraits/men/85.jpg'
    ]
  }),
  methods: {
    show () {
      const viewer = this.$el.querySelector('.images').$viewer
      viewer.show()
    }
  }

}
</script>
