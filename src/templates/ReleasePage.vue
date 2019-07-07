<template>
	<layout :headerSize="1" :footer="false">
		<div style="display: flex; flex-direction: row;">
			<sidebar type="releases" :menu="releasesmenu" />
			<div class="releases__content">
				<div class="releases__content-container">
					<post-layout
						:title="$page.releases.title"
						:description="$page.releases.description"
						:titleBorder="$page.releases.titleBorder"
						:content="$page.releases.content"
					/>
				</div>
			</div>
		</div>
	</layout>
</template>

<script>
import ReleasesMenu from "../../data/releases-menu.json";
import Sidebar from "../components/Sidebar";
import PostLayout from "../layouts/Post";

export default {
	name: "ReleasesPage",
	metaInfo() {
		return {
			title: this.$page.releases.title,
			meta: [
				{
					key: "description",
					name: "description",
					content: this.$page.releases.description
				}
			]
		};
	},
	components: {
		Sidebar,
		PostLayout
	},
	computed: {
		releasesmenu() {
			return ReleasesMenu;
		}
	}
};
</script>

<page-query>
query ReleasePage ($path: String!) {
	releases: releasePage (path: $path) {
		title
		description
		titleBorder
		content
	}
}
</page-query>

<style lang='sass'>
.releases
	&__content
		padding-top: 2rem
		padding-bottom: 2rem
		flex: 1

		&-container
			max-width: 760px
			margin-left: auto
			margin-right: auto
			padding-left: 20px
			padding-right: 20px
</style>
