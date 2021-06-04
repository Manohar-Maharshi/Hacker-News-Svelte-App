<script>
	import Header from './components/Header.svelte'
	import Navbar from './components/navBar.svelte'

</script>
<Header/>
<main>
	<Navbar/>
</main>
<style>
:global(body) {
	background-color: #f4f4f4;
	padding:0 0.3rem;
	margin:0 auto;
}

main {
	margin: 0 auto;
	display: flex;
	align-items: center;
	justify-content: space-between;
	flex-direction: column;
	width: 600px;
}
</style>
<!-- 
	https://api.hackernews.io/news?page=1

	https://api.hackernews.io/newest?page=1

	https://api.hackernews.io/show?page=1
	
	https://api.hackernews.io/jobs?page=1

 -->
