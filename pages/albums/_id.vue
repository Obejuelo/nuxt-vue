<template>
	<div class="container">
		<header>
			<h3 class="title">{{album.title}}</h3>
			<nuxt-link to="/">regresar</nuxt-link>
		</header>
		<div class="columns is-multiline">
			<div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
				<img :src="photo.url" alt="photo.title">
			</div>
		</div>
	</div>
</template>

<script>
	import router from 'vue-router';
	import axios from 'axios';
	import env from '../../config/env';

	export default {
		name: 'AlbumIndPage',
		data(){
			return {
				album: {},
				photos: []
			}
		},
		created: async function(){
			let albumId = this.$route.params.id;

			let album = await axios.get(`${env.endpoint}/albums/${albumId}`);
			this.album = album.data;

			let photo = await axios.get(`${env.endpoint}/albums/${albumId}/photos`);
			this.photos = photo.data;
		}
	}
</script>

<style scoped>
	.container{
		text-align: center;
	}
	
	img{
		border-radius: 10px;
	}
</style>
