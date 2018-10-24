<template>
	<div class="container">
		<header>
			<h3 class="title">Title of albums</h3>
		</header>
		<div class="columns is-multiline">
			<AlbumCard :album="album" v-for="album in albums" :key="album.id"/>
		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	import env from '../config/env';
	import AlbumCard from '../components/AlbumCard';
	export default {
		name: 'IndexPage',
		components:{
			AlbumCard
		},
		data(){
			return{
				albums: []
			} 
		},
		created: async function(){
			let res = await axios.get(`${env.endpoint}/albums`);
			this.albums = res.data;
		}
	}
</script>

<style scoped>
.container{
	text-align: center;
}
</style>
