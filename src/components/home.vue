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
            <h1>Customers</h1>
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
        <v-row class="data-table">
        <v-col cols="md-12">
          <v-row>
            <v-col cols="md-2">
            Customer list
            </v-col>
            <v-col cols="md-6">
            <v-text-field
            label="Search"
            append-icon="mdi-magnify">
          </v-text-field>
          </v-col>
            <v-col cols="md-4">
              <v-row align-content="space-between|space-around">
                <v-col cols="5">
                  <v-btn
                  color="primary"
                  class="ma-2 white--text"
                  small
                >
                  Upload
                  <v-icon
                    right
                    dark
                  >
                    mdi-cloud-upload
                  </v-icon>
                </v-btn>
                </v-col>
                <v-col cols="5">
                  <v-btn
                    color="orange"
                    class="ma-2 white--text"
                    small
                  >
                    DOWNLOAD
                    <v-icon
                      right
                      dark
                    >
                      mdi-cloud-download
                    </v-icon>
                  </v-btn>
                </v-col>
              </v-row>
            </v-col>
          </v-row>
          <v-row>
          <v-col cols="lg-12">
          <v-data-table
            :headers="headers"
            :items="info"
            :items-per-page="10"
            class="elevation-1"
            :footer-props="{
              showFirstLastPage: true,
              firstIcon: 'mdi-arrow-collapse-left',
              lastIcon: 'mdi-arrow-collapse-right',
              prevIcon: 'mdi-minus',
              nextIcon: 'mdi-plus'}"
            >
          <template v-slot:item.status="{ item }">
            <v-chip v-if="item.status == 'Lead'"
              class="ma-2"
              color = "orange"
              text-color="white"
            >
              {{ item.status }}
            </v-chip>
            <v-chip v-else
              class="ma-2"
              color = "green"
              text-color="white"
            >
              {{ item.status }}
            </v-chip>
            
          </template>
          <template v-slot:item.actions="{ item }">
            <v-icon>mdi-pencil {{item.actions}}</v-icon>
            <v-icon>mdi-gmail {{item.actions}}</v-icon>
            <v-icon>mdi-android-messages {{item.actions}}</v-icon>
          </template>
          </v-data-table>
          </v-col>
          </v-row>
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
      customers: [
        ['Accounts'],
        ['Tracker'],
      ],
        items: [
          { title: 'FAQS', icon: 'mdi-home-city' },
          { title: 'Customers', icon: 'mdi-account' },
          { title: 'Tasks', icon: 'mdi-account-group-outline' },
          { title: 'Sales', icon: 'mdi-account-group-outline' },
          { title: 'Staff', icon: 'mdi-account-group-outline' },
          { title: 'Products', icon: 'mdi-account-group-outline' },
        ],
        headers: [
          {
            text: 'First Name',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Surname', value: 'surname' },
          { text: 'Email Address', value: 'email' },
          { text: 'Product', value: 'prod' },
          { text: 'Status', value: 'status' },
          { text: 'Telephone', value: 'tel' },
          { text: 'Actions', value: 'actions' },
        ],
        info: [
          {
            name: 'Mxo',
            surname: 'Duma',
            email: 'mxo@gmail.com',
            prod: 24,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'Ice cream sandwich',
            surname: 237,
            email: 9.0,
            prod: 37,
            status: 'Active Account',
            tel: '0712119359',
          },
          {
            name: 'Eclair',
            surname: 262,
            email: 16.0,
            prod: 23,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'Cupcake',
            surname: 305,
            email: 3.7,
            prod: 67,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'Gingerbread',
            surname: 356,
            email: 16.0,
            prod: 49,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'Jelly bean',
            surname: 375,
            email: 0.0,
            prod: 94,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'Lollipop',
            surname: 392,
            email: 0.2,
            prod: 98,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'Honeycomb',
            surname: 408,
            email: 3.2,
            prod: 87,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'Donut',
            surname: 452,
            email: 25.0,
            prod: 51,
            status: 'Lead',
            tel: '0712119359',
          },
          {
            name: 'KitKat',
            surname: 518,
            email: 26.0,
            prod: 65,
            status: 'Lead',
            tel: '0712119359',
          },
        ],
      }
    },
  }
</script>

<style scoped>
.data-table{
  padding: 20px;
}
.card-container
{
  width: 800px;
}
.v-card{
  width: 1000px;
}
</style>