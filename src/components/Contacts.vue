<template>
  <v-container class="container">
     <div height="auto" width="auto" class="container" fixed>
        <v-row class="text-center">
          <v-col cols="lg-2">
    <v-navigation-drawer
      permanent
      fixed
      src="public/assets/tree-736885__340.webp"
    >
      <template v-slot:prepend>
        <v-list-item two-line>
          <v-list-item-avatar>
            <img src="@/assets/Rod.jpg">
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>Mxo Duma</v-list-item-title>
            <v-list-item-subtitle>Front-End Developer</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item
          v-for="item in items"
          :key="item.title"
        >
          <v-list-item-content v-if="item.title != 'Customers'">
            <v-list-item-title><h1>{{ item.title }}</h1></v-list-item-title>
          </v-list-item-content>
          <v-list-item-content v-else>
          <v-list-group
          :value="true"
          no-action
          sub-group
          >
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><h1>{{ item.title }}</h1></v-list-item-title>
            </v-list-item-content>
          </template>
            <v-list-item
              v-for="([title], i) in customers"
              :key="i"
              link
            >
              <v-list-item-title v-text="title"></v-list-item-title>
            </v-list-item>
            </v-list-group>
          </v-list-item-content>
        </v-list-item>
      </v-list>
        <template class="logout">
            <v-row>
                <v-col cols="12">
                <v-btn
                  color="primary"
                  class="white--text"
                  small
                >
                  Logout
                <v-icon
                    right
                    dark
                  >
                    mdi-logout
                  </v-icon>
                </v-btn>
                </v-col>
              </v-row>
        </template>
    </v-navigation-drawer>
     </v-col>
      <v-col cols="lg-10">
        <v-row align-content="space-between|space-around">
          <v-col cols="lg-12">
          <v-row>
            <v-col cols="lg-2">
            <v-icon>mdi-arrow-down-drop-circle</v-icon>
            </v-col>
            <v-col cols="lg-8">
            <h1>Contacts</h1>
            </v-col>
            <v-col cols="lg-2">
              <v-icon>mdi-card-account-details</v-icon>
            </v-col>
          </v-row>
          <v-row align-content="space-between|space-around">
            <v-divider></v-divider>
          </v-row>
          <v-spacer>
          </v-spacer>
          </v-col>
        </v-row>
        <v-row class="mb-6 data-table">
            <v-col md="4" sm="6">
                <v-row class="avatar">
                    <div class="details">
                    <v-row align-content="center" class="space-around">
                    <v-avatar
                    color="blue"
                    size="56"
                    >
                    <span class="white--text headline">KM</span>
                    </v-avatar>
                        </v-row>
                        <v-row align-content="center">
                            <span>Mxo Duma</span>
                        </v-row>
                        <v-row align-content="center">
                            <span>www.co.za</span>
                        </v-row>
                        <v-row align-content="center" class="space-around">
                            <v-col cols="2">
                            <v-icon
                            >
                            mdi-note
                            </v-icon>
                            <span>Note</span>
                            </v-col>

                            <v-col cols="2">
                            <v-icon
                            >
                            mdi-email
                            </v-icon>
                            <span>Email</span>
                            </v-col>

                           <v-col cols="2">
                            <v-icon
                           
                            >
                            mdi-phone
                            </v-icon>
                            <span>Call</span>
                            </v-col>
                            <v-col cols="2">
                            <v-icon
                            
                            >
                            mdi-plus
                            </v-icon>
                            <span>Log</span>
                            </v-col>
                            <v-col cols="2">
                            <v-icon
                            
                            >
                            mdi-calendar-check
                            </v-icon>
                            <span>Task</span>
                            </v-col>
                            <v-col cols="2">
                            <v-icon
                            
                            >
                            mdi-air-filter
                            </v-icon>
                            <span>Meet</span>
                            </v-col>
                        </v-row>
                    </div>
                </v-row>
                <v-divider></v-divider>
                <v-row class="about">
                    <v-list>
                        <v-list-group
                            :value="true"
                            no-action
                            sub-group
                        >
                            <template v-slot:activator>
                                <v-list-item-content>
                                <v-list-item-title>About this contact</v-list-item-title>
                                </v-list-item-content>
                            </template>
                            <v-list-item
                                v-for="([title, value], i) in about"
                                :key="i"
                                link
                            >
                                <v-list-item-title v-text="title"></v-list-item-title>
                                <v-list-item-title v-text="value"></v-list-item-title>
                            </v-list-item>
                        </v-list-group>
                    </v-list>
                </v-row>
            </v-col>
            <v-col md="8" sm="6">
            <v-card>
    <v-tabs
      v-model="tab"
    >
      <v-tabs-slider></v-tabs-slider>

      <v-tab href="#tab-1">
        Activity
      </v-tab>

      <v-tab href="#tab-2">
        Notes
      </v-tab>

      <v-tab href="#tab-3">
        Emails
      </v-tab>
        <v-tab href="#tab-4">
        Calls
      </v-tab>
        <v-tab href="#tab-5">
        Tasks
      </v-tab>
    <v-tab href="#tab-6">
        Meetings
      </v-tab>
    </v-tabs>

    <v-tabs-items v-model="tab">
      <v-tab-item
        v-for="i in 6"
        :key="i"
        :value="'tab-' + i"
      >
        <v-card flat v-if="i == 5">
          <v-card-text>
              <v-row>
                <v-col cols="12">
                <v-btn
                  color="primary"
                  class="white--text"
                  small
                >
                  Create Task
                </v-btn>
                </v-col>
              </v-row>
            <v-row>
                <v-col cols="12">
                    <span>Create a task for yourself or a teammate. Keep track of all your to-dos for this task.</span>
                </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
        </v-card>
            </v-col>
        </v-row>
      </v-col>
    </v-row>
  </div>
  </v-container>
</template>

<script>
  export default {
    data () {
      return {
          tab: null,
          text:'<div></div>',
      customers: [
        ['Leads'],
        ['Opportunities'],
        ['Accounts'],
      ],
    about: [
        ['First name', 'Mxo'],
        ['Last name', 'Duma'],
        ['Email', 'mxo@ww.co.za'],
      ],
        items: [
          { title: 'FAQs' },
          { title: 'Customers'}, 
          { title: 'Contacts'},
          { title: 'Tasks'},
        ],
        headers: [
          {
            text: 'First Name',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Surname', value: 'calories' },
          { text: 'Email Address', value: 'fat' },
          { text: 'Product', value: 'carbs' },
          { text: 'Status', value: 'protein' },
          { text: 'Telephone', value: 'iron' },
          { text: 'Actions', value: 'actions' },
        ],
        desserts: [
          {
            name: 'Mxo',
            calories: 'Duma',
            fat: 'mxo@gmail.com',
            carbs: 24,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'Ice cream sandwich',
            calories: 237,
            fat: 9.0,
            carbs: 37,
            protein: 'Active Account',
            iron: '0712119359',
          },
          {
            name: 'Eclair',
            calories: 262,
            fat: 16.0,
            carbs: 23,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'Cupcake',
            calories: 305,
            fat: 3.7,
            carbs: 67,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'Gingerbread',
            calories: 356,
            fat: 16.0,
            carbs: 49,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'Jelly bean',
            calories: 375,
            fat: 0.0,
            carbs: 94,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'Lollipop',
            calories: 392,
            fat: 0.2,
            carbs: 98,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'Honeycomb',
            calories: 408,
            fat: 3.2,
            carbs: 87,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'Donut',
            calories: 452,
            fat: 25.0,
            carbs: 51,
            protein: 'Lead',
            iron: '0712119359',
          },
          {
            name: 'KitKat',
            calories: 518,
            fat: 26.0,
            carbs: 65,
            protein: 'Lead',
            iron: '0712119359',
          },
        ],
      }
    },
  }
</script>

<style scoped>
.avatar
{
    padding: auto;
    margin: 5px;
    align-content: center;
}
.about
{
    margin-top: 50px;
}
.logout
{
    bottom: 0px;
}
.scroll-active
{
    overflow-y: scroll;
    height: 500px;
}
.details
{
    padding: 5px;
}
.data-table{
  padding: 20px;
}
.card-container
{
  width: 800px;
}
.v-card{
  height: 500px;
}
</style>