<template>
	<div class="grid h-screen place-content-center gap-3">
		<h1 class="text-5xl text-green-500">Welcome to Nuxt Content V2</h1>
		<p class="text-xl text-neutral-800">
			Visit
			<a href="https://content.nuxtjs.org">content.nuxtjs.org</a>
			for more!
		</p>
		<nuxt-link
			href="/blog"
			class="mx-auto rounded-xl bg-green-500 px-20 py-4 text-white"
		>
			Go to Blog
		</nuxt-link>
	</div>
</template>

<script>
export default {};
</script>

<style></style>
