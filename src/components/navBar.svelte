<script>
	import Card from './Card.svelte';
	let current = '';
	let allNewsArray = []
	const news_url = "https://api.hackernews.io/news?page=1";
	const newest_url = "https://api.hackernews.io/newest?page=1";
	const show_url = "https://api.hackernews.io/show?page=1";
	const jobs_url = "https://api.hackernews.io/jobs?page=1";
	async function getData(url){
		const response = await fetch(url)
		const json = await response.json();
		allNewsArray = []
		json.forEach((item)=>{
			allNewsArray.push(item);
			allNewsArray = allNewsArray;
		})
	}
	const chnageToNews = () =>{
		current = 'News'
		getData(news_url)		
	}
	const chnageToNewest = () =>{
		current = 'Newest'
		getData(newest_url)		


	}
	const chnageToShow = () =>{
		current = 'Show'
		getData(show_url);		
	}
	const chnageToJob = () =>{
		current = 'Job'
		getData(jobs_url);		
	}

</script>

<nav>
	<button
		class:selected="{current === 'News'}"
		on:click="{chnageToNews}">
		News
	</button>

	<button
		class:selected="{current === 'Newest'}"
		on:click="{chnageToNewest}">
		Newest
	</button>

	<button
		class:selected="{current === 'Show'}"
		on:click="{chnageToShow}">
		Show
	</button>
	<button
		class:selected="{current === 'Job'}"
		on:click="{chnageToJob}">
		Job
	</button>

</nav>
<main>
	{#each allNewsArray as news}
		<Card timeOfPost="{news.time_ago}" type="{news.type}" content="{news.title}" userName="{news.user}" userPoints="{news.points}" userCommentCount="{news.comments_count}" linkToArticle="{news.url}"/>
	{/each}
</main>
<style>
	main{
		margin-top:2rem;
	}
	nav{
		display: flex;
		align-items:center;
		justify-content:space-between;
		user-select:none;
	}
	button{
		color:gray;
		text-decoration:none;
		margin-right:2rem;
		outline:none;
		border:none;
		padding:0.1rem 1.1rem;
		background-color:gray;
		color:whitesmoke;
		border:5px;
		transition:0.2s all ease;
		cursor: pointer;
		font-size:1.2rem;
		font-family:inherit;
	}
	button:last-child{
		margin-right:0;
	}
	.selected {
		background-color: lightgray;
		color: gray;
	}
	.sk-folding-cube {
	  margin: 7rem auto;
	  width: 5rem;
	  height: 5rem;
	  position: relative;
	  -webkit-transform: rotateZ(45deg);
	          transform: rotateZ(45deg);
	}

	.sk-folding-cube .sk-cube {
	  float: left;
	  width: 50%;
	  height: 50%;
	  position: relative;
	  -webkit-transform: scale(1.1);
	      -ms-transform: scale(1.1);
	          transform: scale(1.1); 
	}
	.sk-folding-cube .sk-cube:before {
	  content: '';
	  position: absolute;
	  top: 0;
	  left: 0;
	  width: 100%;
	  height: 100%;
	  background-color: gray;
	  -webkit-animation: sk-foldCubeAngle 2.4s infinite linear both;
	          animation: sk-foldCubeAngle 2.4s infinite linear both;
	  -webkit-transform-origin: 100% 100%;
	      -ms-transform-origin: 100% 100%;
	          transform-origin: 100% 100%;
	}
	.sk-folding-cube .sk-cube2 {
	  -webkit-transform: scale(1.1) rotateZ(90deg);
	          transform: scale(1.1) rotateZ(90deg);
	}
	.sk-folding-cube .sk-cube3 {
	  -webkit-transform: scale(1.1) rotateZ(180deg);
	          transform: scale(1.1) rotateZ(180deg);
	}
	.sk-folding-cube .sk-cube4 {
	  -webkit-transform: scale(1.1) rotateZ(270deg);
	          transform: scale(1.1) rotateZ(270deg);
	}
	.sk-folding-cube .sk-cube2:before {
	  -webkit-animation-delay: 0.3s;
	          animation-delay: 0.3s;
	}
	.sk-folding-cube .sk-cube3:before {
	  -webkit-animation-delay: 0.6s;
	          animation-delay: 0.6s; 
	}
	.sk-folding-cube .sk-cube4:before {
	  -webkit-animation-delay: 0.9s;
	          animation-delay: 0.9s;
	}
	@-webkit-keyframes sk-foldCubeAngle {
	  0%, 10% {
	    -webkit-transform: perspective(140px) rotateX(-180deg);
	            transform: perspective(140px) rotateX(-180deg);
	    opacity: 0; 
	  } 25%, 75% {
	    -webkit-transform: perspective(140px) rotateX(0deg);
	            transform: perspective(140px) rotateX(0deg);
	    opacity: 1; 
	  } 90%, 100% {
	    -webkit-transform: perspective(140px) rotateY(180deg);
	            transform: perspective(140px) rotateY(180deg);
	    opacity: 0; 
	  } 
	}

	@keyframes sk-foldCubeAngle {
	  0%, 10% {
	    -webkit-transform: perspective(140px) rotateX(-180deg);
	            transform: perspective(140px) rotateX(-180deg);
	    opacity: 0; 
	  } 25%, 75% {
	    -webkit-transform: perspective(140px) rotateX(0deg);
	            transform: perspective(140px) rotateX(0deg);
	    opacity: 1; 
	  } 90%, 100% {
	    -webkit-transform: perspective(140px) rotateY(180deg);
	            transform: perspective(140px) rotateY(180deg);
	    opacity: 0; 
	  }
	}
</style>
