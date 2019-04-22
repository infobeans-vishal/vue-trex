<template>
    <v-app light>
        <v-toolbar class="deep-purple">
            <v-toolbar-side-icon @click.stop="drawer = !drawer" dark></v-toolbar-side-icon>
            <v-toolbar-title dark>Vuetify Tutorial</v-toolbar-title>
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
                            <v-list-tile-title :to="item.link" @click="redirect">{{ item.title }}</v-list-tile-title>
                        </v-list-tile>
                    </v-list>
                </v-menu>
            </v-toolbar-items>
        </v-toolbar>
        <v-navigation-drawer v-model="drawer" :mini-variant.sync="mini" hide-overlay stateless >
            <v-toolbar flat class="transparent">
                <v-list class="pa-0">
                    <v-list-tile avatar>
                        <v-list-tile-avatar>
                            <img src="https://randomuser.me/api/portraits/men/85.jpg">
                        </v-list-tile-avatar>
                        <v-list-tile-content>
                            <v-list-tile-title>Rohit Khatri</v-list-tile-title>
                        </v-list-tile-content>
                        <v-list-tile-action>
                            <v-btn icon @click.stop="mini = !mini">
                                <v-icon>chevron_left</v-icon>
                            </v-btn>
                        </v-list-tile-action>
                    </v-list-tile>
                </v-list>
            </v-toolbar>

            <v-list class="pt-0" dense>
                <v-divider></v-divider>
                <v-list-group :value="item.active" v-for="item in items" v-bind:key="item.title" :prepend-icon="item.action" no-action >
                    <v-list-tile slot="activator" @click="">
                        <v-list-tile-action>
                            <v-icon>{{ item.icon }}</v-icon>
                        </v-list-tile-action>
                        <v-list-tile-content>
                            <v-list-tile-title>{{ item.title }} active={{ item.active }}</v-list-tile-title>
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
                </v-list-group>
            </v-list>
        </v-navigation-drawer>
        <Content></Content>

        
    </v-app>
</template>

<script>

import Content from './Content'

export default {
    name: 'app-header',
	components: {
        Content
    },
    methods: {
        redirect () {
            alert('ddd');
        }
    },
	data() {
		return {
			drawer: true,
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
			],
			mini: true,
			right: null
		}
	}
}
</script>

<style scoped>
  .tile {
    margin: 5px;
    border-radius: 4px;
  }
  .tile:hover {
    background: green;
  }
  .tile:active {
    background: yellow;
  }
</style>