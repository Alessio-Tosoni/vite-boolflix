<script>
import axios from 'axios';
import {store} from './store.js';

import AppHeader from './components/AppHeader.vue'
import SearchBar from './components/SearchBar.vue';


export default {
	components: {
		AppHeader,
		SearchBar
	},
    data() {
        return {
            store,
			options : {
  			method: 'GET',
  			url: 'https://api.themoviedb.org/3/search/movie',
  			params: {include_adult: 'false', language: 'en-US', page: '1'},
  			headers: {
   			accept: 'application/json',
    		Authorization: 'Bearer ae000a48c3ede78a529a0a8f11fefcb1'
  			}
}

        };
    },
    
	methods: {
		search (){
			axios.request(options)
			.then(function (response) {
		  console.log(response.data);
			})
			.catch(function (error) {
		  console.error(error);
			})

		}
	}
};

</script>

<template>
    <AppHeader />
	<SearchBar @search="search"/>
    
</template>

<style scoped>

</style>