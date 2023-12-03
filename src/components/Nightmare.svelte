<script lang="ts">
	export let Title: string;
	export let Description: string;
	export let Image: string = '/logo.png';
</script>

<svelte:head>
	<title>{Title}</title>
	<meta property="og:title" content={Title} />
	<meta property="og:site_name" content="Popkat CDN" />
	<meta property="og:type" content="website" />
	<meta property="og:url" content="https://popkat.select-list.xyz" />
	<meta property="og:image" content={Image} />
	<meta property="og:description" content={Description} />
</svelte:head>
