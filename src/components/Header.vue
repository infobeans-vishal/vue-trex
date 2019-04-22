<template>
      <v-app id="inspire" light>
         <v-navigation-drawer
            :clipped="drawer.clipped"
            :fixed="drawer.fixed"
            :permanent="drawer.permanent"
            :mini-variant="drawer.mini"
            v-model="drawer.open"
            app
            >
            <v-list >
               <v-list-tile 
                  v-if="!drawer.permanent"
                  @click="makeDrawerPermanent">
                  <v-list-tile-action>
                     <v-icon>chevron_right</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                     <v-list-tile-title>Static Drawer</v-list-tile-title>
                  </v-list-tile-content>
               </v-list-tile>
               <v-list-tile @click="toggleMiniDrawer">
                  <v-list-tile-action>
                     <v-icon>aspect_ratio</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                     <v-list-tile-title>Mini Drawer</v-list-tile-title>
                  </v-list-tile-content>
               </v-list-tile>
               <v-divider></v-divider>
               <v-list-tile v-for="item in items" v-bind:key="item.title" @click="">
                  <v-list-tile-action>
                     <v-icon>{{ item.icon }}</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                     <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                  </v-list-tile-content>
               </v-list-tile>
               <!-- <v-list-group :value="item.active" v-for="item in items" v-bind:key="item.title" :prepend-icon="item.action" no-action >
                  <v-list-tile slot="activator" @click="">
                  	<v-list-tile-action>
                  		<v-icon>{{ item.icon }}</v-icon>
                  	</v-list-tile-action>
                  	<v-list-tile-content>
                  		<v-list-tile-title>{{ item.title }} </v-list-tile-title>
                  	</v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile v-for="subItem in item.items" :key="subItem.title" ripple @click="">
                  	<v-list-tile-action>
                  		<v-icon>{{ subItem.icon }}</v-icon>
                  	</v-list-tile-action>
                  	<v-list-tile-content>
                  		<v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
                  	</v-list-tile-content>
                  </v-list-tile>
                  </v-list-group> -->
            </v-list>
         </v-navigation-drawer>
         <v-toolbar
            app
            :fixed="toolbar.fixed"
            :clipped-left="toolbar.clippedLeft"
            class="deep-purple"
			
            >
            <v-toolbar-side-icon 
               @click.stop="toggleDrawer"
               ></v-toolbar-side-icon>
            <v-toolbar-title>Vuetify Drawer Example</v-toolbar-title>
         </v-toolbar>
         <Content></Content>
         <v-footer app :fixed="footer.fixed" :clipped-left="footer.clippedCenter " class="deep-purple">
            <span class="caption" >&copy;2019 International Code Council, Inc. </span>
         </v-footer>
      </v-app>
</template>

<script>

import Content from './Content'

	export default {
		name: 'app-header',
		components: {
        	Content
    	},
		data: () => ({
			drawer: {
				// sets the open status of the drawer
				open: true,
				// sets if the drawer is shown above (false) or below (true) the toolbar
				clipped: false,
				// sets if the drawer is CSS positioned as 'fixed'
				fixed: false,
				// sets if the drawer remains visible all the time (true) or not (false)
				permanent: true,
				// sets the drawer to the mini variant, showing only icons, of itself (true) 
				// or showing the full drawer (false)
				mini: true
			},
			toolbar: {
				//
				fixed: true,
				// sets if the toolbar contents is leaving space for drawer (false) or not (true)
				clippedLeft: false
			},
			footer: {
				// sets the CSS position of the footer
				fixed: true,
				// sets if the footer is full width (true) or gives space to the drawer (false)
				clippedLeft: true
			},
			header_menu: [{
                    title: 'Profile',
                    link: '/profile'
				},
				{
                    title: 'Change Password',
                    link: '/change-password'
				},
				{
                    title: 'Logout',
                    link: '/logout'
				}
			],
			items: [{
					title: 'Dashboard',
					active: true,
					icon: 'dashboard',
				},
				{
					title: 'Certifications',
					icon: 'dashboard',
					active: false,
					items: [{
							title: 'Search Certification',
							icon: 'search',
						},
						{
							title: 'List Certification Applications',
							icon: 'dashboard',
						},
						{
							title: 'List Renewal Applications',
							icon: 'dashboard',
						},
						{
							title: 'List Pending Manual Review',
							icon: 'dashboard',
						},
						{
							title: 'List Rules',
							icon: 'dashboard',
						},
						{
							title: 'Master Data',
							icon: 'dashboard',
						}
					]
				},
				{
					title: 'Exams',
					icon: 'list_alt',
					items: [{
							title: 'Add Exam'
						},
						{
							title: 'List Exams'
						},
						{
							title: 'Master Data'
						}

					]
				},
				{
					title: 'Code Editions',
					icon: 'menu',
					items: [{
							title: 'Add Code Edition'
						},
						{
							title: 'List Code Editions'
						}
					]
				},
				{
					title: 'Jurisdictions',
					items: [{
							title: 'Add Jurisdiction'
						},
						{
							title: 'List Jurisdictions'
						}

					]
				},
				{
					title: 'Jurisdiction Contacts',
					icon: 'contacts',
					items: [{
							title: 'Add Jurisdiction Contact'
						},
						{
							title: 'List Jurisdiction Contacts'
						}

					]
				},
				{
					title: 'Exam Sites',
					icon: 'public',
					items: [{
							title: 'Add Exam Site'
						},
						{
							title: 'List Exam Sites'
						}
					]
				},
				{
					title: 'Site Contacts',
					icon: 'public',
					items: [{
							title: 'Add Site Contact'
						},
						{
							title: 'List Site Contacts'
						}
					]
				},
				{
					title: 'Site Proctors',
					icon: 'public',
					items: [{
							title: 'Add Site Proctor'
						},
						{
							title: 'List Site Proctors'
						}
					]
				},
				{
					title: 'Letters',
					icon: 'mail',
					items: [{
							title: 'Add Letter'
						},
						{
							title: 'List Letters'
						},
						{
							title: 'Individual Confirmation Letter'
						},
						{
							title: 'Site Confirmation Letter'
						},
						{
							title: 'Proctor Confirmation Letter'
						},
						{
							title: 'Exam Confirmation Letter'
						}
					]
				},
				{
					title: 'Candidates',
					icon: 'person',
					items: [{
							title: 'Add Candidate'
						},
						{
							title: 'List Candidates'
						},
						{
							title: 'List All Transcripts'
						},
						{
							title: 'Master Data'
						}
					]
				},
				{
					title: 'Eligibilities'
				},
				{
					title: 'Score Roster',
					icon: 'score'
				},
				{
					title: 'Score Summary'
				},
				{
					title: 'Review Anomalies',
					icon: 'person',
					items: [{
							title: 'List Candidate Anomalies'
						},
						{
							title: 'List Transcript Anomalies'
						}
					]
				},
				{
					title: 'Reports',
					icon: 'report',
					items: [{
							title: 'Reporting Tool'
						},
						{
							title: 'List of participants Report'
						},
						{
							title: 'Participants Count Report'
						},
						{
							title: 'Sign-In Sheet Report'
						},
						{
							title: 'Answer Sheet Report'
						},
						{
							title: 'Site Report'
						},
						{
							title: 'Number Of Exams Given Report'
						}
					]
				},
				{
					title: 'Import Export',
					icon: 'face'
				}
			]
		}),

		props: {
			source: String
		},

		methods: {
			// changes the drawer to permanent
			makeDrawerPermanent() {
				this.drawer.permanent = true
				// set the clipped state of the drawer and toolbar
				this.drawer.clipped = false
				this.toolbar.clippedLeft = false
			},
			// toggles the drawer variant (mini/full)
			toggleMiniDrawer() {
				this.drawer.mini = !this.drawer.mini
			},
			// toggles the drawer type (permanent vs temporary) or shows/hides the drawer
			toggleDrawer() {
				if (this.drawer.permanent) {
					this.drawer.permanent = !this.drawer.permanent
					// set the clipped state of the drawer and toolbar
					this.drawer.clipped = true
					this.toolbar.clippedLeft = true
				} else {
					// normal drawer
					this.drawer.open = !this.drawer.open
				}
			}
		}

	} 
</script>