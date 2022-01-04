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
                      <h2 class="display-2">Generate A New Payment Link List </h2>
                    </v-flex>
   
                  </v-layout>
                </v-flex>

              </v-layout>
              <v-layout class="mt-36px">
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
                        <v-text-field
                          label="PROPERTY"
                        ></v-text-field>
                                
                        </v-list-tile>
                        <v-list-tile>
                          <v-text-field
                          label="TENANT">
                          </v-text-field>
     
                        </v-list-tile>
                        <v-list-tile>
                        <v-select
                        :items="items1"
                        label="INITIATOR"
                        
                      ></v-select>
                        </v-list-tile>
   
                        <v-list-tile>
                       <v-menu
                          ref="menu1"
                          v-model="menu1"
                          :close-on-content-click="false"
                          :nudge-right="40"
                          :return-value.sync="date"
                          lazy
                          transition="scale-transition"
                          offset-y
                          full-width
                          min-width="290px"
                        >
                          <template v-slot:activator="{ on }">
                            <v-text-field
                              v-model="date"
                              label="CREATED DATE FROM"
                              prepend-icon="event"
                              readonly
                              v-on="on" 
                            class="re-datepicker"
                            ></v-text-field>
                          </template>
                          <v-date-picker v-model="date" no-title scrollable>
                            <v-spacer></v-spacer>
                            <v-btn flat color="primary" @click="menu1 = false">Cancel</v-btn>
                            <v-btn flat color="primary" @click="$refs.menu1.save(date)">OK</v-btn>
                          </v-date-picker>
                        </v-menu>
     
                        </v-list-tile>
                           <v-list-tile>
                       <v-menu
                          ref="menu2"
                          v-model="menu2"
                          :close-on-content-click="false"
                          :nudge-right="40"
                          :return-value.sync="date1"
                          lazy
                          transition="scale-transition"
                          offset-y
                          full-width
                          min-width="290px"
                        >
                          <template v-slot:activator="{ on }">
                            <v-text-field
                              v-model="date1"
                              label="CREATED DATE TO"
                              prepend-icon="event"
                              readonly
                              v-on="on" 
                            class="re-datepicker"
                            ></v-text-field>
                          </template>
                          <v-date-picker v-model="date1" no-title scrollable>
                            <v-spacer></v-spacer>
                            <v-btn flat color="primary" @click="menu2 = false">Cancel</v-btn>
                            <v-btn flat color="primary" @click="$refs.menu2.save(date1)">OK</v-btn>
                          </v-date-picker>
                        </v-menu>
     
                        </v-list-tile>
                        <v-list-tile>
                            <v-text-field
                              label="YEAR"
                            ></v-text-field>
                        </v-list-tile>
                        <v-list-tile>
                          <v-select
                            :items="items2"
                            label="MONTH"
                            
                          ></v-select>
                        </v-list-tile>
                        <v-list-tile>
                          <v-select
                            :items="items3"
                            label="STATUS"
                            
                          ></v-select>
                        </v-list-tile>
                      <v-list-tile>
                       <v-menu
                          ref="menu3"
                          v-model="menu3"
                          :close-on-content-click="false"
                          :nudge-right="40"
                          :return-value.sync="date2"
                          lazy
                          transition="scale-transition"
                          offset-y
                          full-width
                          min-width="290px"
                        >
                          <template v-slot:activator="{ on }">
                            <v-text-field
                              v-model="date2"
                              label="PAID DATE FROM"
                              prepend-icon="event"
                              readonly
                              v-on="on" 
                            class="re-datepicker"
                            ></v-text-field>
                          </template>
                          <v-date-picker v-model="date2" no-title scrollable>
                            <v-spacer></v-spacer>
                            <v-btn flat color="primary" @click="menu3 = false">Cancel</v-btn>
                            <v-btn flat color="primary" @click="$refs.menu3.save(date2)">OK</v-btn>
                          </v-date-picker>
                        </v-menu>
     
                        </v-list-tile>
                         <v-list-tile>
                       <v-menu
                          ref="menu4"
                          v-model="menu4"
                          :close-on-content-click="false"
                          :nudge-right="40"
                          :return-value.sync="date3"
                          lazy
                          transition="scale-transition"
                          offset-y
                          full-width
                          min-width="290px"
                        >
                          <template v-slot:activator="{ on }">
                            <v-text-field
                              v-model="date3"
                              label="PAID DATE TO"
                              prepend-icon="event"
                              readonly
                              v-on="on" 
                            class="re-datepicker"
                            ></v-text-field>
                          </template>
                          <v-date-picker v-model="date3" no-title scrollable>
                            <v-spacer></v-spacer>
                            <v-btn flat color="primary" @click="menu4 = false">Cancel</v-btn>
                            <v-btn flat color="primary" @click="$refs.menu4.save(date3)">OK</v-btn>
                          </v-date-picker>
                        </v-menu>
     
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
                        <tr @click="dialog=true">
                        <td >
                          {{ props.item.id }}
                        </td>
                        <td class="min-width190" >{{ props.item.created}}</td>
                        <td >{{ props.item.initiator }}</td>
                        <td >{{ props.item.contractId }}</td>
                        <td>
                          {{ props.item.property }}
                        </td>
                        <td class="min-width125">{{ props.item.unitType }}</td>
                        <td >{{ props.item.unitNumber }}</td>
                        <td >{{ props.item.tenant }}</td>
                        <td >{{ props.item.month }}</td>
                        <td >{{ props.item.year }}</td>
                        <td >{{ props.item.amount }}</td>
                        <td >{{ props.item.status }}</td>
                        <td  class="min-width190">{{ props.item.paidDate }}</td>
                        </tr>
                      </template>
                    </v-data-table>
                    </div>
               
              </v-card>

                 
             
            </v-flex>
          </v-layout>
        </v-layout>
 <template>
          <div class="text-xs-center">
            <v-dialog
              v-model="dialog"
              width="420"
            >
        
              <v-card>
                <v-card-title
                  class="headline d-flex justify-space-between form-title"
                  primary-title
                
                >
                <span class="text-start">
                 Generate A New Payment Link List
                </span>
                <v-icon class="d-flex justify-end"  @click="dialog = false">
                  close
                </v-icon>
                </v-card-title>
        
                <v-card-text>


                     
                        
                        <v-list dense>
                          <v-list-tile>
                            <v-list-tile-content>ID</v-list-tile-content>
                            <v-list-tile-content class="align-end orange-c">A1</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Created</v-list-tile-content>
                            <v-list-tile-content class="align-end">1/Jan/2021 13:00:00 AM</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Initiator</v-list-tile-content>
                            <v-list-tile-content class="align-end orange-c">User1</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Contract Id</v-list-tile-content>
                            <v-list-tile-content class="align-end">1</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Property</v-list-tile-content>
                            <v-list-tile-content class="align-end">Mazaya</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Unit Type</v-list-tile-content>
                            <v-list-tile-content class="align-end">2 Bed rooms</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Unit Number</v-list-tile-content>
                            <v-list-tile-content class="align-end">1</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Tenant</v-list-tile-content>
                            <v-list-tile-content class="align-end orange-c">Mohamed</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content> Month</v-list-tile-content>
                            <v-list-tile-content class="align-end">12</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content> Year</v-list-tile-content>
                            <v-list-tile-content class="align-end">2021</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Amount</v-list-tile-content>
                            <v-list-tile-content class="align-end">200</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Status</v-list-tile-content>
                            <v-list-tile-content class="align-end">Paid</v-list-tile-content>
                          </v-list-tile>
                          <v-list-tile>
                            <v-list-tile-content>Paid Date</v-list-tile-content>
                            <v-list-tile-content class="align-end">2 Jan 2021 10:00:30 AM</v-list-tile-content>
                          </v-list-tile>
                        </v-list>


                </v-card-text>
        
               

              </v-card>
            </v-dialog>
          </div>
        </template>

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
          date:"",
          menu1:false,
          date1:"",
          menu2:false,
          date2:"",
          menu3:false,
          menu4:false,
          date3:"",
          dialog:false,
          items: [
            {
              text: "Dashboard",
              disabled: false,
              href: "#",
            },
            {
              text: "Generate A New Payment Link List",
              disabled: true,
              href: "#",
            },
          ],
          items1:["User1","User2"],
          items2:["January", "February","March","April","May","June","July","Auguest","September","October","November","December"],
          items3:["Paid", "Not Paid"],
          edititems:[{title:"Terminate Contract"},{title: "Renew Contract"}],
          headers: [
            {
              text: "ID",
              align: "left",
              sortable: false,
            },
            { text: "CREATED", align: "left", sortable: false },
            { text: "INITIATOR", align: "left", sortable: false },
            { text: "CONTRACT ID", align: "left", sortable: false },
            { text: "PROPERTY", align: "left", sortable: false },
            { text: "UNIT TYPE", align: "left", sortable: false },
            { text: "UNIT NUMBER", align: "left", sortable: false },
            { text: "TENANT", align: "left", sortable: false },
            { text: "MONTH", align: "left", sortable: false },
            { text: "YEAR", align: "left", sortable: false },
            { text: "AMOUNT", align: "left", sortable: false },
            { text: "STATUS", align: "left", sortable: false },
            { text: "PAID DATE", align: "left", sortable: false }
          ],
          units: [
            {
              id: "1",
              created: "Jan 2021 10:00:30 AM",
              initiator: "User1",
              contractId:"1",
              property:"Mazaya",
              unitType: "2 Bed rooms",
              unitNumber:"1",
              tenant:"Mohamed",
              month:"12",
              year:"2021",
              amount:"200",
              status:"Paid",
              paidDate:"Jan 2021 10:00:30 AM"
            },
            {
              id: "2",
              created: "Jan 2021 10:00:30 AM",
              initiator: "User2",
              contractId:"2",
              property:"Alya",
              unitType: "3 Bed rooms",
              unitNumber:"2",
              tenant:"Ahmed",
              month:"12",
              year:"2021",
              amount:"250",
              status:"Not Paid",
              paidDate:""
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
.min-width125{
    min-width:125px
}
.min-width190{
    min-width:190px
}
.mt-36px{
  margin-top:36px;
}
</style>