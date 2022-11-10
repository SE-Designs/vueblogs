<template>
	<main class="bg-white px-4 pt-16 pb-20 sm:px-6 lg:px-8 lg:pt-24 lg:pb-28">
		<div class="lg:max-w-7x mx-auto max-w-lg">
			<div class="border-b border-b-gray-200 pb-6">
				<h2
					class="text-3xl font-semibold tracking-tight text-gray-900 sm:text-4xl"
				>
					Recent Posts
				</h2>
			</div>
			<div class="mt-12 grid gap-16 lg:grid-cols-3 lg:gap-x-5 lg:gap-y-12">
				<div
					v-for="article in qc"
					:key="article._path"
					class="flex flex-col justify-between rounded-lg border border-gray-200 p-4"
				>
					<nuxt-link :to="article._path">
						{{ article.title }}
						<h2 class="text-xl text-gray-900"></h2>
						<p class="mt-3 text-gray-500">
							{{
								article.description.length > 77
									? article.description.substring(0, 77) + "..."
									: article.description
							}}
						</p>
					</nuxt-link>
					<div class="mt-6">
						<a
							:href="`?author=${article.author}`"
							class="text-sm font-medium text-gray-900"
						>
							{{ article.author }}
						</a>
						<div class="text-sm text-gray-500">
							<time datetime="2020-03-16">
								{{ convertDate(article.date) }}
							</time>
						</div>
					</div>
				</div>
			</div>
		</div>
	</main>
</template>

<script setup>
import { convertDate } from "~~/utils";
const { query } = useRoute();
const { author } = query;
console.log({ author });

const qc = await queryContent("blog")
	.where({ author })
	.sort({ _file: 1, $numeric: true })
	.find();
</script>

<style></style>
