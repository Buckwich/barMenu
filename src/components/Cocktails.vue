<template>
  <v-container fluid grid-list-sm>
    <v-layout wrap>
      <v-flex v-for="card in cards" :key="card.name" xs12 sm6 md4>
        <!-- <v-card>
          <v-img
            :src="require('../assets/cocktails/'+card.image)"
            class="white--text"
            height="200px"
            gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
          >
            <v-card-title class="fill-height align-end" v-text="card.name"></v-card-title>
          </v-img>

          <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn flat>Details</v-btn>
          </v-card-actions>
        </v-card>-->
        <!-- <v-card>
          <v-list-item three-line>
            <v-list-item-avatar width="100" height="200" tile left>
              <v-img :src="require('../assets/cocktails/'+card.image)"></v-img>
            </v-list-item-avatar>
            <v-list-item-content class="align-self-start">
              <v-list-item-title class="headline mb-2" v-text="card.name"></v-list-item-title>

              <v-list-item-subtitle v-text="card.description"></v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-card>-->
        <v-card style="height:100%">
          <v-container style="height:100%">
            <v-layout style="overflow:hidden; height:100%">
              <v-flex shrink>
                <v-img
                  :src="require('../assets/cocktailsSmall/' + card.image)"
                  height="100%"
                  width="100"
                ></v-img>
              </v-flex>
              <v-flex class="align-self-start">
                <v-card-title
                  class="fill-height align-end"
                  v-text="card.name"
                ></v-card-title>
                <v-card-text>
                  <v-list-item-group>
                    <v-list-item
                      dense
                      v-for="(amount, ingredient) in card.recipe"
                      :key="card.name + ingredient"
                    >
                      <v-list-item-action disabled>
                        <v-checkbox color="primary"></v-checkbox>
                      </v-list-item-action>

                      <v-list-item-content
                        >{{ amount }} {{ ingredient }}</v-list-item-content
                      >
                    </v-list-item>
                  </v-list-item-group>
                  <!-- <v-list-item-title
                    v-for="(amount, ingredient) in card.recipe"
                    :key="card.name+ingredient"
                  >{{ingredient}}:{{amount}}</v-list-item-title>-->
                </v-card-text>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import cocktails from "./cocktails";
console.log(cocktails);
export default {
  props: ["category"],
  data: () => ({
    settings: [],
  }),
  computed: {
    cards() {
      if (this.category == "") {
        return cocktails.cocktails;
      } else {
        return cocktails.cocktails.filter((cocktail) => {
          return cocktail.category.includes(this.category);
        });
      }
    },
  },
};
</script>
