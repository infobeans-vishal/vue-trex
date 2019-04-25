<template>
   <v-content>
            <v-container>
              <div style="margin-top:20px;margin-bottom:10px;
                -webkit-box-shadow: inset 0 1px 0 #ffffff;
                -moz-border-radius: 5px;
                border-radius: 3px;
                border:1px solid #ddd;
                width:100%;
                ">
                <v-breadcrumbs :items="breadcrumbs">
                <template v-slot:item="props">
                  <a :href="props.item.href" :class="[props.item.disabled && 'disabled']">{{ props.item.text.toUpperCase() }}</a>
                </template>
              </v-breadcrumbs>
              </div>
              <Dashboard></Dashboard>
            </v-container>
         </v-content>
</template>

<script>

import Dashboard from './Dashboard';

  export default {
    components: {
      Dashboard
    },

    data () {
      return {
        breadcrumbs: [
        {
          text: 'Dashboard',
          disabled: false,
          href: 'breadcrumbs_dashboard'
        },
        {
          text: 'Link 1',
          disabled: false,
          href: 'breadcrumbs_link_1'
        },
        {
          text: 'Link 2',
          disabled: true,
          href: 'breadcrumbs_link_2'
        }
      ],
      }
    }
  }
</script>

<style>
.v-breadcrumbs {
  padding: 10px;
}
.v-breadcrumbs a {
  text-decoration: none !important;  
  color: green;
  font-size: 12px;

}
</style>
