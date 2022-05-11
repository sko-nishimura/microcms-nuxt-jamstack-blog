<template>
<header>
	<div class="siteName">Site Name</div>
	<div class="headerNav">
		<globalNav />
	</div>
</header>
</template>


<script>
import globalNav from '@/components/globalNav.vue'
export default {
	components: {
		globalNav
	}

}
</script>

<style lang="scss" scoped>
	header{
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: rem(100);
		padding: 0 4%;
		border-bottom: 1px solid #ccc;
		.siteName{
			font-size: 2em;
		}
	}
</style>