<template>
  <v-card>
    <v-card-title
      class="card-title"
    >
      <p v-if="showSubCategories==false" class="text--secondary">
        Category
      </p>
      <p v-else class="text--secondary">
        <v-icon
          medium
          class="mr-2"
          color="primary"
          @click="goBack"
        >
          mdi-chevron-left
        </v-icon>
        Sub-category
      </p>
      <v-text-field
        append-icon="mdi-magnify"
        placeholder="Search a product"
        class="col-lg-4 col-sm-4 col-md-4 mt-4 search-input"
        filled
        rounded
        dense
      />
    </v-card-title>
    <v-card-text justify="center" align="center">
      <v-row>
        <v-col
          cols="12"
          lg="12"
          md="12"
          sm="12"
        >
          <v-card
            class="main-cat-card"
            elevation="0"
          >
            <v-card-text>
              <v-row v-if="showSubCategories==false">
                <v-col
                  v-for="(category,index) in categories"
                  :key="index"
                  cols="12"
                  lg="2"
                  sm="2"
                  md="2"
                  xl="2"
                >
                  <div @click="getSubCategories(index)">
                    <v-card
                      elevation="0"
                      class="card-values pr-1 pl-1"
                      :class="{ active : category.isActive }"
                    >
                      <v-card-text class="pt-5 pr-0 pl-0">
                        <div class="cat-values mb-2">
                          <v-icon
                            class="cat-values-icon"
                            color="primary"
                            x-large
                          >
                            mdi-view-grid
                          </v-icon>
                        </div>
                        <p class="category-text">
                          {{ category.title }}
                        </p>
                      </v-card-text>
                    </v-card>
                  </div>
                </v-col>
              </v-row>
              <div v-else>
                <SubCategory :subCategories="subCategories"/>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import SubCategory from './SubCategory.vue'
export default {
    name: "CategoryComponent",
    components: { SubCategory },
    data() {
        return {
            showSubCategories: false,
            categories: [],
            subCategories: []
        }
    },
    mounted() {
        this.initialize();
        this.showSubCategories = false;
    },
    methods: {
        initialize() {
            this.categories = [
                {
                    id: 1,
                    title: "Appliances",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" }
                    ]
                },
                {
                    id: 2,
                    title: "Arts, Crafts & Sewings",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 3,
                    title: "Automotive",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 4,
                    title: "Baby Products",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 5,
                    title: "Beaty & Personal Care",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                { id: 6, title: "Books", isActive: false, subCategories: [] },
                {
                    id: 7,
                    title: "Cell phone & Accessories",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 8,
                    title: "Appliances",
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 9,
                    title: "Arts, Crafts & Sewings",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 10,
                    title: "Automotive",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 11,
                    title: "Baby Products",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 12,
                    title: "Beaty & Personal Care",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 13,
                    title: "Books",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                },
                {
                    id: 14,
                    title: "Cell phone & Accessories",
                    isActive: false,
                    subCategories: [
                        { id: 1, title: "Sub-Category" },
                        { id: 2, title: "Sub-Category" },
                        { id: 3, title: "Sub-Category" },
                        { id: 4, title: "Sub-Category" }
                    ]
                }
            ];
        },
        getSubCategories(index) {
            for (let i = 0; i < this.categories.length; i++) {
                this.categories[i].isActive = false;
            }
            if (this.categories[index]) {
                this.categories[index].isActive = true;
            }
            this.subCategories = this.categories[index].subCategories;
            this.showSubCategories = true;
        },
        goBack() {
            this.showSubCategories = false;
        }
    },
}
</script>

<style scoped>
.search-input{
  font-weight: normal !important;
}
.card-title{
  display: flex;
  justify-content: space-between !important;
  padding-top: 0px !important;
  padding-bottom: 0px !important;
}
div.main-cat-card{
    background-color:rgb(0 0 255 / 3%) !important;
}
.cat-values{
    background-color:#EAF3FD !important;
    color: blue;
    width: 45px;
    height: 45px;
    margin: 0 auto;
    border-radius: 50%;
    font-size: 85px !important;
}
.cat-values{
    position: relative;
    margin-top: -10px;
}
.card-values{
    height: 110px;
    max-height: 115px;
    margin: 0px !important;
}
.active{
    cursor: pointer;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px !important;
    background-color: #fff;
}
.card-values:hover{
    cursor: pointer;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px !important;
}

button.mdi-chevron-left{
  background-color: #EAF3FD;
}
</style>
