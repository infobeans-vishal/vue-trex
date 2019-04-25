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
                     <v-icon >chevron_right</v-icon>
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
               <!-- <v-list-tile v-for="item in items" v-bind:key="item.title" @click="">
                  <v-list-tile-action>
                     <v-icon>{{ item.icon }}</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                     <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                  </v-list-tile-content>
               </v-list-tile>
                -->

		<v-list-group :prepend-icon="item.icon" v-for="item in items" v-bind:key="item.title">
			<template v-slot:activator>
				<v-list-tile >
					<v-list-tile-title>{{item.title}}</v-list-tile-title>
				</v-list-tile>
			</template>
			<v-list-group :prepend-icon="subItem.icon" sub-group no-action v-for="subItem in item.items" :key="subItem.title">
				<template v-slot:activator>
					<v-list-tile>
						<v-list-tile-title>{{subItem.title}}</v-list-tile-title>
					</v-list-tile>
				</template>
			</v-list-group>
		</v-list-group>
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
			<v-spacer></v-spacer>
			<v-toolbar-items>
                <v-menu offset-y>
                    <template v-slot:activator="{ on }">
                        <v-btn icon v-on="on">
                            <v-avatar size="40" color="grey lighten-4">
                                <img src="https://randomuser.me/api/portraits/men/85.jpg">
                            </v-avatar>
                        </v-btn>
                    </template>
                    <v-list>
                        <v-list-tile v-for="(item, index) in header_menu" :key="index" >
                            <v-list-tile-title :to="item.link">{{ item.title }}</v-list-tile-title>
                        </v-list-tile>
                    </v-list>
                </v-menu>
            </v-toolbar-items>
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
					icon: 'home',
					link: '/'
				},
				{
					title: 'Certifications',
					icon: 'dashboard',
					active: false,
					items: [{
							title: 'Search Certification',
							icon: 'search',
							link: '/certificates',

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
							icon: 'storage',
						}
					]
				},
				{
					title: 'Exams',
					icon: 'list_alt',
					items: [{
							title: 'Add Exam',
							icon: 'add_circle'
						},
						{
							title: 'List Exams',
							icon: 'list'
						},
						{
							title: 'Master Data',
							icon: 'storage',
						}

					]
				},
				{
					title: 'Code Editions',
					icon: 'menu',
					items: [{
							title: 'Add Code Edition',
							icon: 'add_circle'
						},
						{
							title: 'List Code Editions',
							icon: 'list'
						}
					]
				},
				{
					title: 'Jurisdictions',
					items: [{
							title: 'Add Jurisdiction',
							icon: 'add_circle'
						},
						{
							title: 'List Jurisdictions',
							icon: 'list'
						}

					]
				},
				{
					title: 'Jurisdiction Contacts',
					icon: 'contacts',
					items: [{
							title: 'Add Jurisdiction Contact',
							icon: 'add_circle'
						},
						{
							title: 'List Jurisdiction Contacts',
							icon: 'list'
						}

					]
				},
				{
					title: 'Exam Sites',
					icon: 'public',
					items: [{
							title: 'Add Exam Site',
							icon: 'add_circle'
						},
						{
							title: 'List Exam Sites',
							icon: 'list'
						}
					]
				},
				{
					title: 'Site Contacts',
					icon: 'public',
					items: [{
							title: 'Add Site Contact',
							icon: 'add_circle'
						},
						{
							title: 'List Site Contacts',
							icon: 'list'
						}
					]
				},
				{
					title: 'Site Proctors',
					icon: 'public',
					items: [{
							title: 'Add Site Proctor',
							icon: 'add_circle'
						},
						{
							title: 'List Site Proctors',
							icon: 'list'
						}
					]
				},
				{
					title: 'Letters',
					icon: 'mail',
					items: [{
							title: 'Add Letter',
							icon: 'add_circle'
						},
						{
							title: 'List Letters',
							icon: 'list'
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
							title: 'Add Candidate',
							icon: 'add_circle'
						},
						{
							title: 'List Candidates',
							icon: 'list'
						},
						{
							title: 'List All Transcripts',
							icon: 'list'
						},
						{
							title: 'Master Data',
							icon: 'storage',
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
							title: 'List Candidate Anomalies',
							icon: 'list'
						},
						{
							title: 'List Transcript Anomalies',
							icon: 'list'
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
							title: 'List of participants Report',
							icon: 'list'
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

<style>
.v-list__group__header__prepend-icon .v-icon {
    color: purple;
} 

.v-input__icon--append .v-icon { 
    color: purple;
}

</style>

