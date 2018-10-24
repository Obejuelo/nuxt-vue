<template>
	<div class="column is-one-quarter">
		<div class="box">
			<h3>{{album.title}}</h3>
			<nuxt-link class="button is-small is-info" :to="`/albums/${album.id}`" >Ver más</nuxt-link>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'AlbumCard',
		props: {
			album: Object
		}
	}
</script>

<style scoped>
	.box{
		text-align: center;
	}
	h3{
		min-height: 5em;
	}
</style>
