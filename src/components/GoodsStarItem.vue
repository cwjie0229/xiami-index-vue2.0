<template>
	<div class="recommend-container">
		<div class="recommend-header">
			<h2 class="title">小米明星单品</h2>
			<div class="control-part">
				<span
					@click="slidePre"
					class="control control-left"
					:class="{'disable': this.currPage === 0}">
					<i class="fa fa-chevron-left icon-arrow"></i>
				</span>
				<span
					@click="slideNext"
					class="control control-right"
					:class="{'disable': this.currPage === Math.floor((this.recomends.length - 1) / 5)}">
					<i class="fa fa-chevron-right icon-arrow"></i>
				</span>
			</div>
		</div>
		<div class="recommend-wrap">
			<ul class="recommend-content clearfix">
				<li class="recomend-item-Start-list"
					v-for="item in recomends">
					<a :href="item.sourceUrl" target="_blank">
						<img class="item-image" :src="item.imgUrl" alt="" />
						<h3 class="item-name">{{item.name}}</h3>
                        <p class="item-favorable">
							{{item.favorable}}
						</p>
						<p class="item-price">
							{{item.price}}元
						</p>
						
					</a>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
import $ from 'jQuery';
export default {
	data () {
		return {
			currPage: 0,
			evtNextStatus: true,
			evtPreStatus: true,
			recomends: [
				{sourceUrl: '//item.mi.com/1154300011.html', imgUrl: 'http://i3.mifile.cn/a4/e991f1e2-20d8-40c3-bf1d-012b122c986b', name: '小米5s Plus', price: '2299', favorable: '5.7英寸大屏双摄手机，拍照黑科技'},
				{sourceUrl: '//item.mi.com/1153300030.html', imgUrl: 'http://i3.mifile.cn/a4/fad1b5c4-2f91-4802-ae7a-670eb42a42a1', name: '小米电视3s 55英寸', price: '3999', favorable: '人工智能电视，4K大屏新旗舰'},
				{sourceUrl: '//item.mi.com/1155100006.html', imgUrl: 'http://i3.mifile.cn/a4/17fc57e5-e332-4452-bba4-ef341f6e59fd', name: '小米移动电源2', price: '79', favorable: '双向快充，高密度锂聚合物电芯'},
				{sourceUrl: '//item.mi.com/1154100018.html', imgUrl: 'http://i3.mifile.cn/a4/6ef55907-bbed-49be-a2bb-be0821b5f7b8', name: '小米手环 2', price: '149', favorable: 'OLED 显示屏幕，升级计步算法'},
				{sourceUrl: '//item.mi.com/1155100011.html', imgUrl: 'http://i3.mifile.cn/a4/04d4fc22-ffab-4b9c-8a25-701c09e3bd6e', name: '米家恒温电水壶', price: '199', favorable: '快速沸腾，水温智能控制'},
				{sourceUrl: '//item.mi.com/1154900069.html', imgUrl: 'http://i3.mifile.cn/a4/0906bec7-68ad-41e9-9617-fb6550725a85 ', name: '米家 LED 智能台灯', price: '169', favorable: '无可视频闪，亮度色温无级调节'},
				{sourceUrl: '//item.mi.com/1162100021.html', imgUrl: 'http://i3.mifile.cn/a4/c8c48bbb-5c57-4fa6-9bea-7abd7f24a13a', name: '米家iHealth血压计', price: '399', favorable: '爸妈上手就会用的智能血压计'},
				{sourceUrl: '//item.mi.com/1153700018.html', imgUrl: 'http://i3.mifile.cn/a4/de35852a-1be5-4ef5-846f-dcdd2efcfea6', name: '小米路由器3', price: '149', favorable: '更快更强，不止四天线'},
				{sourceUrl: '//item.mi.com/1161200004.html', imgUrl: 'http://i3.mifile.cn/a4/eb09500f-bad2-43de-8b94-2cc17c30de71', name: '小米活塞耳机 清新版', price: '29', favorable: '铝合金音腔，第三代平衡阻尼系统'},
				{sourceUrl: '//item.mi.com/1153300025.html', imgUrl: 'http://i3.mifile.cn/a4/d663ce13-c814-4f35-a7a8-46a4745e6fd7', name: '小米体重秤', price: '99', favorable: '100克，喝杯水都可感知的精准'},
				 
			]
		}
	},
	methods: {
		slideNext () {
			if (this.currPage < Math.floor((this.recomends.length - 1) / 5)) {
				this.currPage++
				$('.recommend-content').css('margin-left', this.currPage * (-1224) + 'px')
			}
		},
		slidePre () {
			if (this.currPage !== 0) {
				this.currPage--
				$('.recommend-content').css('margin-left', this.currPage * (-1224) + 'px')
			}
		}
	}
}
</script>

<style>
.recommend-container {
	width: 1226px;
	height: auto;
	margin: 0 auto;
}

.recommend-header {
	position: relative;
	
}

.recommend-header .title {
    margin: 0;
    font-size: 22px;
    font-weight: 200;
    line-height: 58px;
    color: #333;
}
.recommend-header .control-part {
    position: absolute;
    top: 10px;
    right: 0;
    float: left;
    display: block;
}

.recommend-header .control-part .control {
			display: block;
			float: left;
			width: 34px;
			height: 23px;
			line-height: 23px;
			text-align: center;
			border: 1px solid #e0e0e0;
			cursor: pointer;
		}
.recommend-header .control-part .control:hover {
    .icon-arrow {
        color: #ff6700;
    }
}


.recommend-header .control-part .control.disable:hover .icon-arrow {
            color: #e0e0e0;
        }
        
    
    .recommend-header .control-part .control.disable .icon-arrow {
        color: #e0e0e0;
    }

.recommend-header .control-part .control .icon-arrow {
    color: #b0b0b0;
    font-size: 10px;
}



.recommend-wrap {
	width: 1226px;
	height: 310px;
	overflow: hidden;
}
.recommend-content {
	width: auto;
	height: 300px;
	transition: all 0.3s;
}
.recommend-content  .recomend-item-Start-list {
    float: left;
    display: block;
    width: 234px;
    height: 300px;
    margin: 0 13px 14px 0;
    font-size: 14px;
    background: #fff;
    cursor: pointer;
    transition: all 0.3s;
    border-top-width: 1px;
    border-top-style: solid;
}
.recommend-content  .recomend-item-Start-list:nth-last-child(5n+1) {
    margin-right: 0;
}
.recommend-content  .recomend-item-Start-list .item-image {
    display: block;
    width: 140px;
    height: 140px;
    margin: 40px auto 15px;
}
.recommend-content  .recomend-item-Start-list .item-name {
    margin-bottom: 10px;
    font-weight: normal;
    font-size: 14px;
    text-align: center;
    color: #333;
}
.recommend-content  .recomend-item-Start-list .item-price {
    margin-bottom: 10px;
    font-size: 14px;
    text-align: center;
    color: #ff6700;
}
    .recommend-content  .recomend-item-Start-list .item-favorable {
    font-size: 14px;
    text-align: center;
    color: #757575;
}
.recommend-content  .recomend-item-Start-list:nth-child(1){
       border-top-color: #ffac13;
}
.recommend-content  .recomend-item-Start-list:nth-child(2){
     border-top-color: #83c44e;
}
.recommend-content  .recomend-item-Start-list:nth-child(3){
       border-top-color: #2196f3;
}
.recommend-content  .recomend-item-Start-list:nth-child(4){
       border-top-color: #e53935;
}
.recommend-content  .recomend-item-Start-list:nth-child(5){
       border-top-color: #00c0a5;
}
.recommend-content  .recomend-item-Start-list:nth-child(6){
       border-top-color: #ffac13;
}
.recommend-content  .recomend-item-Start-list:nth-child(7){
       border-top-color: #83c44e;
}
.recommend-content  .recomend-item-Start-list:nth-child(8){
       border-top-color: #2196f3;
}
.recommend-content  .recomend-item-Start-list:nth-child(9){
       border-top-color: #e53935;
}
.recommend-content  .recomend-item-Start-list:nth-child(10){
       border-top-color: #00c0a5;
}
</style>
