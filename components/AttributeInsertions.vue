<template>
  <v-card elevation="2" class="rounded-lg">
    <v-container>
      <v-card-title class="d-inline-block">
        <div class="text--secondary">
          Attributes*
        </div>
        <div class="text-subtitle-0 text--disabled text-sm-body-2">
          You can add one or more attribute for product.
        </div>
      </v-card-title>
      <v-row class="pa-4">
        <v-row>
          <v-col
            v-for="(e,index) in elementsData"
            :key="index"
            cols="12"
            md="3"
            lg="3"
            sm="3"
          >
            <v-card elevation="0" outlined class="ma-1 pt-1 pb-7">
              <v-row class="pt-5 pl-7 d-flex h-card">
                <div class="text--secondary">
                  Attribute {{ index+1 }}
                </div>
                <v-icon
                  class="mr-4 card-close-btn"
                  @click="removeCardAttr(index)"
                >
                  mdi-close
                </v-icon>
              </v-row>
              <v-card-text class="d-inline-block mt-2">
                <div class="text--secondary">
                  Attribute Name
                </div>
                <v-text-field
                  placeholder="Name"
                  filled
                  class="w-full"
                  rounded
                  dense
                />
                <div class="text--secondary">
                  Attribute Value
                </div>
                <v-text-field
                  :key="index"
                  :ref="`val${index}`"
                  v-model="e.value"
                  placeholder="Value"
                  filled
                  rounded
                  dense
                  append-icon="mdi-plus"
                  @keydown.enter="addValue(index)"
                  @click:append="addValue(index)"
                />
                <v-row class="d-flex">
                  <div class="scroll-wrapper">
                    <v-chip
                      v-for="(attr,i) in e.values"
                      :key="i"
                      class="pr-6 mr-1 ml-1"
                      close
                      @click:close="removeValue(i,index)"
                    >
                      {{ attr }}
                    </v-chip>
                  </div>
                </v-row>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12" md="3" lg="3" sm="3">
            <v-card elevation="0" outlined class="ma-1 pt-11 pb-11 add-card" @click="addNewAttrForm">
              <v-card-text class="card-items d-inline-block">
                <v-btn
                  class="ma-2 add-attr-btn"
                  outlined
                >
                  <v-icon>mdi-plus</v-icon>
                </v-btn>
                <p class="add-attr-txt">
                  Add another attribute
                </p>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
// import FormComponent from './FormComponent.vue'

export default {
  name: 'AttributeInsertions',
  data () {
    return {
      elements: 0,
      elementsData: [{ attribute: '', values: [], value: null }]
    }
  },
  methods: {
    addNewAttrForm () {
      this.elements++
      this.elementsData.push({ attribute: '', values: [] })
    },

    addValue (i) {
      this.elementsData[i].values.push(this.elementsData[i].value)
      this.elementsData[i].value = ''
    },

    removeValue (i, index) {
      this.elementsData[index].values.splice(i, 1)
    },
    removeCardAttr (i) {
      this.elementsData.splice(i, 1)
    }
  }
}
</script>

<style>
div.v-card{
  border-radius: 10px !important;
}
button.v-icon{
    background-color: rgb(76, 76, 250);
    border-radius: 50%;
    padding: 2px;
    margin-right: -20px !important;
}

button.mdi-plus{
    color: #fff !important;
}
button.mdi-close-circle{
    background-color:transparent;
    color: rgb(176, 176, 253) !important;
}
.add-card{
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    height: 44vh;
}
.add-attr-btn{
    border-color: rgb(179, 179, 179);
    color:rgb(179, 179, 179) !important;
}
.add-attr-txt{
    color:rgb(179, 179, 179);
    font-weight: bold;
}
.add-card:hover{
    cursor: pointer;
}
.add-card:hover .add-attr-btn{
    cursor:pointer;
    background-color: #0d47a1;
    color:#FFF !important;
    border: 1px solid #0d47a1;
}

.add-card:hover .add-attr-txt{
    color:#0d47a1;
    font-weight: bold;
}
.h-card{
  display: flex;
  justify-content: space-between;
}

button.card-close-btn{
  cursor: pointer;
  background-color: transparent;
  margin-top: -10px;
}
button.card-close-btn:hover{
  color:#0d47a1;
  background-color: transparent !important;
}
span.v-chip{
  background-color: transparent !important;
  border: 1px solid #eee;
}
.scroll-wrapper{
  height: 5.1vh;
  padding-top: 2px;
  padding-bottom:3px;
  max-height: 5.1vh;
  width: 100%;
  overflow-x: auto;
}
</style>
