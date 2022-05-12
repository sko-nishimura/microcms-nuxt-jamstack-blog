<template>
<header>
	<div class="siteName">Site Name</div>
	<div class="headerNav">
		<button class="headerNav__toggle" v-bind:class="{open:isOpen}" @click="isOpen=!isOpen"><span></span></button>
		<globalNav />
	</div>
</header>
</template>


<script>
import globalNav from '@/components/globalNav.vue'
export default {
	components: {
		globalNav
	},
	data: () => ({
		isOpen: false
	})

}
</script>

<style lang="scss" scoped>
	header{
		display: flex;
		justify-content: space-between;
		align-items: center;
		position: relative;
		height: 5em;
		padding: 0 4%;
		border-bottom: 1px solid #ccc;
		.siteName{
			font-size: 2em;
		}
	}
	.headerNav__toggle{
		display: flex;
		justify-content: center;
		align-items: center;
		position: absolute;
		right: 0;
		top: 0;
		width: 5em;
		height: 5em;
		background-color: $mainColor;
		font-size: 1em;
		span{
			display: block;
			position: relative;
			width: 60%;
			height: 3px;
			background-color: #666;
			border-radius: 1rem;
			transition: .5s;
			&::before,&::after{
				display: block;
				position: absolute;
				left: 0;
				top: 0;
				width: 100%;
				height: 100%;
				background: #666;
				transition: .5s;
				content: "";
			}
			&::before{
				transform: rotate(0) translateY(-400%);
				animation: barToggleTopReverse .8s;
			}
			&::after{
				transform: rotate(0) translateY(400%);
				animation: barToggleBottomReverse .8s;
			}
		}
		&.open{
			span{
				background-color: transparent;
				&::before{
					transform: rotate(-45deg) translateY(0);
					animation: barToggleTop .8s;
				}
				&::after{
					transform: rotate(45deg) translateY(0);
					animation: barToggleBottom .8s;
				}
			}
		}
	}

	@keyframes barToggleTop {
  0% {
    transform: rotate(0) translateY(-400%);
  }
  50% {
    transform: rotate(0) translateY(0);
  }
  100% {
    transform: rotate(-45deg) translateY(0);
  }
}

@keyframes barToggleBottom {
  0% {
    transform: rotate(0) translateY(400%);
  }
  50% {
    transform: rotate(0) translateY(0);
  }
  100% {
    transform: rotate(45deg) translateY(0);
  }
}

@keyframes barToggleTopReverse {
  0% {
    transform: rotate(-45deg) translateY(0);
  }
  50% {
    transform: rotate(0) translateY(0);
  }
  100% {
    transform: rotate(0) translateY(-400%);
  }
}

@keyframes barToggleBottomReverse {
  0% {
    transform: rotate(45deg) translateY(0);
  }
  50% {
    transform: rotate(0) translateY(0);
  }
  100% {
    transform: rotate(0) translateY(400%);
  }
}
</style>