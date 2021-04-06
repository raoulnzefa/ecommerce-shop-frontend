<template>
  <div class="home">
    <v-app>
      <v-container>
        <v-row class="mb-5">
          <v-col cols="12" md="4">
            <v-text-field label="Search items" prepend-icon="mdi-magnify" icon="red" error></v-text-field>
          </v-col>

          <v-spacer></v-spacer>

          <span class="red--text mt-9 mx-3">{{ products.length }} items</span>

          <v-btn text class="mt-7">
            <v-icon color="red" class="mx-3">mdi-menu</v-icon>
          </v-btn>
          <v-btn text class="mt-7">
            <v-icon color="red" class="mx-3">mdi-view-dashboard</v-icon>
          </v-btn>
        </v-row>

        <v-row class="text-center">
          <v-col xl="3" lg="4" md="6" xs="12" v-for="product in products" :key="product.id" class="mb-10">
            <v-hover v-slot:default="{ hover }">
              <v-card width="100%" min-height="400px" align="center">
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn icon>
                    <v-icon>mdi-pencil</v-icon>
                  </v-btn>
                </v-card-actions>
                <v-img :src="'https://' + product.imageUrl" width="100%" height="270px" style="margin-top:-51px"></v-img>
                <v-card-text class="red--text">{{ product.name }}</v-card-text>
                <v-card-text class="red--text font-weight-black"><span class="text-decoration-line-through caption mr-2" v-if="product.price.previous.text">{{ product.price.previous.text }}</span>{{ product.price.current.text }}</v-card-text>
                <v-expand-transition>
                  <div v-if="hover" class="d-flex transition-fast-in-fast-out red v-card-reveal display-3 white--text" style="height:100%">
                    <v-btn outlined color="white">Details</v-btn>
                  </div>
                </v-expand-transition>
                <v-btn absolute color="red" class="white--text" fab large left top>
                  <h1>{{ (Math.floor(product.id / 1000000)) }}</h1>
                </v-btn>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'Home',
  data(){
    return {
      products: undefined
    }
  },
  mounted() {
    const options = {
      method: 'GET',
      url: 'https://asos2.p.rapidapi.com/products/v2/list',
      params: {
        offset: '0',
        categoryId: '4209',
        limit: '48',
        store: 'US',
        country: 'US',
        currency: 'USD',
        sort: 'freshness',
        lang: 'en-US',
        sizeSchema: 'US'
      },
      headers: {
        'x-rapidapi-key': '33d05ab973mshbed0cbad31809e8p1670fcjsne0a172ca1188',
        'x-rapidapi-host': 'asos2.p.rapidapi.com'
      }
    };

    axios.request(options).then((response) => {
      console.log(response.data);
      this.products = response.data.products;
    }).catch((error) => {
      console.error(error);
    });
    
  },
}
</script>

<style scoped>
.v-card-reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.4;
  position: absolute;
  width: 100%;
}
</style>