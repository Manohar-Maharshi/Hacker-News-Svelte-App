<script>
	export let timeOfPost;
	export let type;
	export let content;
	export let userName;
	export let userPoints;
	export let userCommentCount;
	export let linkToArticle;
</script>
<div class="card">
	<div class="meta">
		<small>time: {timeOfPost}</small>
		/
		<small>type: {type}</small>
	</div>
	<p class="title">{content}</p>
	<div class="additional">
		<p class="user">{userName}</p>
		<p class="points">{userPoints} points</p>
		<p class="comments">{userCommentCount} comments</p>
	</div>
	<a class="link" target="_blank" href="{linkToArticle}">go to article</a>
</div>
<style>
	.card{
		padding:0.6rem 1rem;
		background-color:lightgray;
		position: relative;
		transition:0.2s all ease-in;
		width:800px;
		margin-bottom:1.5rem;
	}
	.meta{
		text-transform:uppercase;
		font-weight:bold;
		color:gray;
		font-size:0.6rem;
	}
	.additional{
		display: flex;
		align-items:center;
	}
	.additional p{
		background-color:gray;
		margin-right:1rem;
		padding:0.15rem 0.5rem;
		color:lightgray;
		font-size:0.7rem;
	}
	.title{
		margin:0.8rem 0;
		margin-top:0.5rem;
		font-weight:bold;
		color:gray;
		font-size:1.5rem;
	}
	.link{
		visibility:hidden;
		color:lightgray;
		text-decoration:none;
		text-transform:uppercase;
		font-weight:bold;
		position: absolute;
		bottom:0;
		right:0;
		background-color:gray;
		padding:0.4rem 1rem;
		transition:0.1s all ease-out;
	}
	.link:hover,.link:focus{
		text-decoration:underline;
	}
	.card:hover .link{
		visibility:visible;
	}
</style>
