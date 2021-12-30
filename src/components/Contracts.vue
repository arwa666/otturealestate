/* eslint-disable vue/valid-v-bind */
<template>
  <div class="rent-mangement">
              <v-layout  wrap justify-center>
          <v-layout  wrap justify-center>
            <v-flex xs12 sm12 lg10>
              <v-layout class="pt-5"  wrap>
                <v-flex grow pa-1 xs10 md8>
                  <v-layout align-start wrap>
                    <v-flex xs12 md12>
                      <h2 class="display-2">Shortly Expired Contracts </h2>
                    </v-flex>
   
                  </v-layout>
                </v-flex>

              </v-layout>
              <v-layout>
                <v-flex pa-1>
                  <v-breadcrumbs :items="items" class="margin-top40">
                    <template v-slot:divider>
                      <v-icon>fiber_manual_record</v-icon>
                    </template>
                  </v-breadcrumbs>
                </v-flex>
              </v-layout>

              <v-card>
                <v-toolbar class="re-toolbar re-wrap">
                  <div class="re-flex">
                    Rows Per Page
                    <v-radio-group v-model="row" class="re-radios"
                      ><v-radio label="all" value="radio-1"></v-radio>
                    </v-radio-group>
                  </div>
                  <v-spacer></v-spacer>
                  <v-text-field
                    hide-details
                    placeholder="Search"
                    single-line
                  ></v-text-field>

                  <v-spacer></v-spacer>

                  <v-btn  dark class="re-full"
                    >EXPORT</v-btn
                  >
                  <!-- <v-btn color="warning" dark class="re-orangtbtn">FILTER <v-icon right>filter_list</v-icon></v-btn> -->
                  <v-menu
                    v-model="menu"
                    :close-on-content-click="false"
                    :nudge-width="200"
                    offset-x
                    class="re-filter"
                  >
                    <template v-slot:activator="{ on }">
                      <v-btn
                        
                        dark
                        class="re-orangtbtn re-full"
                        v-on="on"
                      >
                        FILTER <v-icon right>filter_list</v-icon>
                      </v-btn>
                    </template>

                    <v-card class="pb-4">
                      <v-list>
                        <v-list-tile avatar>
                          <v-list-tile-content>
                            <v-list-tile-title>FILTER</v-list-tile-title>
                          </v-list-tile-content>

                          <v-list-tile-action>
                            <v-btn icon @click="menu = false">
                              <v-icon> close </v-icon>
                            </v-btn>
                          </v-list-tile-action>
                        </v-list-tile>
                      </v-list>

                      <v-divider></v-divider>

                      <v-list>
                        <v-list-tile>
                            
                                Contracts expire within 
                            
                                <v-text-field
                                class="pos"
                                label="30"
                                outline
                                style="width:60px; border-radius:5px"
                                ></v-text-field>
                                Days
                        </v-list-tile>
                        <v-list-tile>
                          <v-text-field
                          label="PROPERTIES">
                          </v-text-field>
     
                        </v-list-tile>

                        <v-list-tile>
                          <v-text-field
                          label="TENANT">
                          </v-text-field>
                        </v-list-tile>

                      </v-list>

                      <v-card-actions>
                        <v-spacer></v-spacer>

                        <v-btn  dark class="re-orangtbtn"
                          >SEARCH</v-btn
                        >
                        <v-btn
                          
                          flat
                          @click="menu = false"
                          class="re-gray-btn re-box-shadow"
                          >RESET</v-btn
                        >
                      </v-card-actions>
                    </v-card>
                  </v-menu>
                </v-toolbar>
                 <div style="overflow:auto">
                      <v-data-table
                      :headers="headers"
                      :items="units"
                      class=" re-table"
                      :pagination.sync="pagination"
                      hide-actions
                    >
                      <template v-slot:items="props">
                        <td >
                          {{ props.item.contract }}
                        </td>
                        <td >{{ props.item.property}}</td>
                        <td class="min-width125">{{ props.item.unitType }}</td>
                        <td >{{ props.item.unitNumber }}</td>
                        <td>
                          {{ props.item.tenant }}
                        </td>
                        <td >{{ props.item.phone }}</td>
                        <td >{{ props.item.email }}</td>
                        <td >{{ props.item.contractStartDate }}</td>
                        <td >{{ props.item.contractEndDate }}</td>
                        <td >{{ props.item.pending }}</td>
                        <td >{{ props.item.amount }}</td>
                        <td class="text-xs-center hoverable-list hoverable">
                            <v-menu offset-y >
                                <template v-slot:activator="{ on }">
                                <v-icon v-on="on">more_horiz</v-icon>
                                </template>
                                <v-list>
                                <v-list-tile
                                    class=" hoverable-list"
                                    v-for="(edititem, index) in edititems"
                                    :key="index"
                                
                                >
                                    <v-list-tile-title
                                    >{{ edititem.title }}</v-list-tile-title
                                    >
                                </v-list-tile>
                                </v-list>
                            </v-menu>
                        </td>
                      </template>
                    </v-data-table>
                    </div>
               
              </v-card>

                 
             
            </v-flex>
          </v-layout>
        </v-layout>


  </div>
</template>


<script>
import '@/assets/css/common.css';
import '@/assets/css/style.css';
export default {
  name: 'Contracts',

        data: () => ({
          drawer: null,
          pagination: {},
          menu: false,
          expand:true,
          row:"",
          on:{},
          items: [
            {
              text: "Dashboard",
              disabled: false,
              href: "#",
            },
            {
              text: "Shortly Expired Contracts",
              disabled: true,
              href: "#",
            },
          ],
          edititems:[{title:"Terminate Contract"},{title: "Renew Contract"}],
          headers: [
            {
              text: "CONTRACT",
              align: "left",
              sortable: false,
            },
            { text: "PROPERTY", align: "left", sortable: false },
            { text: "UNIT TYPE", align: "left", sortable: false },
            { text: "UNIT NUMBER", align: "left", sortable: false },
            { text: "TENANT", align: "left", sortable: false },
            { text: "PHONE", align: "left", sortable: false },
            { text: "EMAIL", align: "left", sortable: false },
            { text: "CONTRACT START DATE", align: "left", sortable: false },
            { text: "CONTRACT END DATE", align: "left", sortable: false },
            { text: "PENDING", align: "left", sortable: false },
            { text: "AMOUNT", align: "left", sortable: false },
            { text: "ACTION", align: "left", sortable: false }
          ],
          units: [
            {
              contract: "1",
              property: "Mazaya",
              unitType: "2 Bed Room",
              unitNumber:"1",
              tenant:"Mohamed",
              phone: "09988775",
              email:"mohamed@gmail.com",
              contractStartDate:"1 Jan 2021",
              contractEndDate:"1 Jan 2022",
              pending:"400",
              amount:"200",
            },

            {
              contract: "2",
              property: "Alya",
              unitType: "3 Bed Room",
              unitNumber:"2",
              tenant:"Ahmed",
              phone: "09988775",
              email:"mohamed@gmail.com",
              contractStartDate:"1 Jan 2021",
              contractEndDate:"1 Jan 2022",
              pending:"400",
              amount:"200"
            },
          ]
    
        }),
        methods:{
                expandFunc: function() {
                    this.expand = !this.expand;
                },
                beforeMount(){
                this.expandFunc()
            },
            },

        props: {
          source: String,
        },

}
</script>

<style scoped>

.v-text-field--box >>> .v-label, .v-text-field--full-width >>> .v-label, .v-text-field--outline >>> .v-label{
    left:50%!important;
    transform: translateX(-50%)!important;
}
.v-text-field--box >>> .v-label--active, .v-text-field--full-width >>> .v-label--active, .v-text-field--outline >>> .v-label--active{
    transform: translateY(-6px) translateX(-50%) scale(.75)!important;
    
}
.pos{
    margin-left:10px!important;
    margin-right:10px!important;
}
.v-text-field--outline.pos >>> .v-input__control >.v-input__slot{
    border-top-right-radius: 4px!important;
    border-bottom-right-radius: 4px!important;
}
.min-width125{
    min-width:125px
}
.margin-top40{
    margin-top:40px;
}
</style>