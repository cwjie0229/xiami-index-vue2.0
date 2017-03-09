<template>
    <div >
		<div><GoodsStarItem></GoodsStarItem></div>
		<div class="goods-container">
			<GoodsTopBox></GoodsTopBox>
			<GoodsCollocation></GoodsCollocation>
			<GoodsAccessories></GoodsAccessories>
			<GoodsAround></GoodsAround>
			<Recommend></Recommend>
			<HotProduct></HotProduct>
			<GoodsContent></GoodsContent>
			
		</div>
	</div>
</template>

<script>
import GoodsStarItem from './GoodsStarItem'
import GoodsTopBox from './GoodsTopBox'
import GoodsCollocation from './GoodsCollocation'
import GoodsAccessories from './GoodsAccessories'
import GoodsAround from './GoodsAround'
import Recommend from './Recommend'
import HotProduct from './HotProduct'
import GoodsContent from './GoodsContent'


export default {
	components: {
		GoodsStarItem,GoodsTopBox,GoodsCollocation,GoodsAccessories,
		GoodsAround,Recommend,HotProduct,GoodsContent
	}
}
</script>

<style>
.goods-container {
	width: 100%;
	height: auto;
	background: #f5f5f5;
	padding-bottom: 40px;
}
</style>