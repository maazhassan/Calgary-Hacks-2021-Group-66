<template>
	<div>
		<md-app>
			<md-app-toolbar class="p-0">
				<nav class="flex w-full py-8 px-6 bg-white shadow justify-between">
					<div>
						<button @click="showSidebar = !showSidebar">
				        	<svg class="w-8 h-8 align-middle inline-block" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
							</svg>
				      	</button>
						<h1 class="text-3xl align-middle font-bold inline-block">BetterD2L</h1>
					</div>
					<div class="text-xl font-semibold pr-4 pl-2">Hello, {{ firstName }} {{ lastName }}</div>
				</nav>
			</md-app-toolbar>
			<md-app-drawer :md-active.sync="showSidebar" md-persistent="full" class="bg-blue-600">
				<nav class="h-full bg-blue-600 z-50 w-full">
					<section class="px-4 py-6">
						<div class="grid grid-cols-2 gap-4">
							<div class="py-16 bg-blue-500 rounded-lg text-white text-center">
								<router-link style="color: white;" to="/calendar" class="text-lg font-bold text-white">
									<svg class="w-6 h-6 align-top inline-block" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
									  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
									</svg>
								Calendar</router-link>
							</div>
							<div class="py-16 bg-blue-500 rounded-lg text-white text-center">
								<router-link style="color: white;" to="/checklist" class="text-lg font-bold text-white">
									<svg class="w-6 h-6 align-top inline-block" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
									  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-6 9l2 2 4-4" />
									</svg>
								Checklist</router-link>
							</div>
							<div class="py-16 bg-blue-500 rounded-lg text-white text-center">
								<router-link style="color: white;" to="/communication" class="text-lg font-bold text-white">
									<svg class="w-6 h-6 align-top inline-block" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
									  <path d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z" />
									</svg>
								Quizzes</router-link>
							</div>
							<div class="py-16 bg-blue-500 rounded-lg text-white text-center">
								<router-link style="color: white;" to="/dropbox" class="text-lg font-bold text-white">
									<svg class="w-6 h-6 align-top inline-block" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
									  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12" />
									</svg>
								Dropbox</router-link>
							</div>
							<div class="py-16 bg-blue-500 rounded-lg text-white text-center">
								<router-link style="color: white;" to="/config" class="text-lg font-bold text-white">
									<svg class="w-6 h-6 align-top inline-block" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
									</svg>
								Shell Configuration</router-link>
							</div>
						</div>
					</section>
				</nav>
			</md-app-drawer>
			<md-app-content class="p-0">
				<section class="bg-gray-200 min-h-screen">
					<section>
						<div style="right: 2rem; bottom: 13rem;" v-if="showChat" class="rounded bg-white h-96 w-80 fixed shadow-lg">
							<div class="flex justify-between bg-blue-600 rounded-t text-blue-100 px-4 py-4 font-semibold">
								<span>Mental Health Check</span>
								<button class="text-white" @click="showChat = false">
									<svg class="w-4 h-4" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
									  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
									</svg>
								</button>
							</div>
							<div class="h-64 py-6">
								
							</div>
							<div>
								<input class="border-t w-full focus:outline-none py-4 px-2" type="text" placeholder="Enter a message">
							</div>
						</div>
						<button style="right: 2rem; bottom: 8rem;" @click="showChat = !showChat" class="focus:outline-none hover:bg-blue-500 text-center rounded-full w-16 h-16 bg-blue-600 fixed shadow">
							<svg class="ml-2 w-12 h-12 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" />
							</svg>
						</button>
					</section>
					<router-view></router-view>
				</section>
			</md-app-content>
		</md-app>
	</div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
			showSidebar: false,
			showChat: false,
			firstName: 'DevCoP',
			lastName: 'Student'
		};
	},

	created() {
		var config = {
			method: 'get',
			url: 'https://devcop.brightspace.com/d2l/api/lp/1.28/users/whoami',
			headers: { 
				'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6IjYzYzc5ZjIzLWZiMTAtNGI4YS1hMjdlLWI4YTc4NGJmNWI5MCJ9.eyJpc3MiOiJodHRwczovL2FwaS5icmlnaHRzcGFjZS5jb20vYXV0aCIsImF1ZCI6Imh0dHBzOi8vYXBpLmJyaWdodHNwYWNlLmNvbS9hdXRoL3Rva2VuIiwiZXhwIjoxNjEzMjkxODkwLCJuYmYiOjE2MTMyODgyOTAsInN1YiI6IjE5NSIsInRlbmFudGlkIjoiNTI3MzEzMTctMzcyYS00ZGI0LWI0OWQtNDk1MDJjZTQzZjJiIiwiYXpwIjoiNWQyNzQ1MGYtMmNlOS00ZGNlLTk1NzAtMGIyMzQ1ODBkZmRkIiwic2NvcGUiOiJjb250ZW50Oio6KiBjb3JlOio6KiBkYXRhaHViOio6KiBkaXNjdXNzaW9uczoqOiogZW5yb2xsbWVudDoqOiogZ3JhZGVzOio6KiBxdWl6emluZzoqOiogcmVwb3J0aW5nOio6KiByb2xlOio6KiB1c2VyczoqOioiLCJqdGkiOiIwZjE0NjNmYy1jNzUxLTRjNmQtYTZmMS0yZmFmNjU1NGFlMjQifQ.RVyr11FfBbSoWHJ9gO4sLffGSyFeGQGI12BaQd5jftc1WSxW8vbGnHeh78HPNO6E-5yA0sz7aU2Z-9BrATDZ8PRec6A-cGKfr0MJJxeQT92XRaapXx84xo3w1yb0CL2x6H7Lgc7Nd6EQ0y9dv-ab_ALe_DBhtybPc5ArWIaWJKTMU6AfSeLBT02rjhjMitdjClQRUoqpcBuARCCnFmWa7m32TahWsu-mU10CsWnKgaw57nitHxNplIkc0d2x_e1JG1VVLWekx8yBFtt270SaxpgWKLoKhSD39xQTeSIl0EqdTOgmpZNXf-gWsNLJGBlGdwZTDCX02XOJnZmePL3FWQ',
	  			'Cookie': 'ADRUM=s=1613250634620&r=https%3A%2F%2Fdevcop.brightspace.com%2Fd2l%2FsystemCheck%2Fwidget%3F0; d2lSessionVal=TKH40vprvvlOxHs5ZGSliFnXb; d2lSecureSessionVal=Y2iwueXFvbe2Ygxmc183PA5zw'
			}
		}

		axios(config)
		.then((response) => {
		  this.firstName = response.data.FirstName;
		  this.lastName = response.data.LastName;
		})
		.catch((error) => {
		  console.log(error);
		});
	}
}
</script>