<template>
	<nav class="globalNav">
		<ul class="menu">
			<li><a href="/about/">About</a></li>
			<li><a href="/news/">News</a></li>
			<li><a href="/contact/">Contact</a></li>
		</ul>
	</nav>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
	.globalNav {
		position: fixed;
		right: 0;
		top: 5em;
		width: 100%;
		height: 100vh;
		background-color: rgba($mainColor,1);
		transform: translateX(100%);
		transition: .5s;
		z-index: 1000;
		.menu{
			display: flex;
			flex-direction: column;
			padding: 2em 0;
			li{
				border-bottom: 1px solid #ccc;
				a{
					display: flex;
					align-items: center;
					height: 4em;
					padding: 0 1.5em;
					font-size: 1rem;
				}
			}
		}
	}
	.open+.globalNav{
		transform: translateX(0);
	}
</style>