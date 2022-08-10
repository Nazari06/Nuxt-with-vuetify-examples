<template>
<v-row>
    <v-col
        v-for="(sub,index) in this.subCategories"
        :key="index"
        cols="12"
        lg="2"
        sm="2"
        md="2"
        xl="2"
    >
        <v-card
            elevation="0"
            class="card-values pr-1 pl-1"
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
                {{ sub.title }}
                </p>
            </v-card-text>
        </v-card>
    </v-col>
</v-row>
</template>

<script>
export default {
    name: 'SubCategories',
    props: [ 'subCategories' ],
}
</script>

<style scoped>
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
.card-values:hover{
    cursor: pointer;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px !important;
}
</style>
