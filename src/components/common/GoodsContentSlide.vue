<template>
	<div class="content"
		:class="content.type">
		<h3 class="title">{{content.title}}</h3>
		<div class="slide-wrap">
			<span
				@click="slidePre(content.index)"
				class="slide-pre">
				<i class="fa fa-chevron-left fa-fw icon-chevron-left"></i>
			</span>
			<span
				@click="slideNext(content.index)"
				class="slide-next">
				<i class="fa fa-chevron-right fa-fw icon-chevron-right"></i>
			</span>
			<ul class="sub-content clearfix"
				:style="{'margin-left': this.currPage * (-296) + 'px'}">
				<li class="content-item"
					v-for="item in content.list">
					<template v-if="item.type === 0">
						<a :href="item.sourceUrl" target="_blank">
							<h3 class="subTitle">{{item.title}}</h3>
							<p class="desc first-desc">
								{{item.desc}}
							</p>
							<img class="content-image" :src="item.imgUrl" alt="" />
						</a>
					</template>
					<template v-if="item.type === 1">
						<a :href="item.sourceUrl" target="_blank">
							<h3 class="subTitle">{{item.title}}</h3>
							<p class="desc">
								{{item.desc}}
							</p>
							<p class="price">
								{{item.price}}
							</p>
							<img class="content-image" :src="item.imgUrl" alt="" />
						</a>
					</template>
					<template v-if="item.type === 2">
						<p class="desc">
							{{item.desc1}}<br/>{{item.desc2}}
						</p>
						<a :href="item.sourceUrl" target="_blank">
							<p class="btn-txt">
								{{item.btnTxt}}
							</p>
						</a>
						<img class="content-image" :src="item.imgUrl" alt="" />
					</template>
				</li>
			</ul>
			<div class="btn-list">
				<ul class="dot-list">
					<li class="dot-item" v-for="item in content.list.length" :class="{'active': this.currPage === 0 }" >
						<span class="dot"></span>
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script>
import $ from 'jQuery';
export default {
	data () {
		return {
			currPage: 0
		}
	},
	props: {
		content: {
			require: true,
			type: Object
		}
	},
	mounted:function(){
        $(".dot-list").eq(0).find("li:first-child").addClass("active")
		$(".dot-list").eq(1).find("li:first-child").addClass("active")
		$(".dot-list").eq(2).find("li:first-child").addClass("active")
		$(".dot-list").eq(3).find("li:first-child").addClass("active")
    },
	methods: {
		slidePre (index) {
			if (this.currPage !== 0) {
				this.currPage--
				$(".dot-list").eq(index).find("li").removeClass("active")
				$(".dot-list").eq(index).find("li").eq(this.currPage).addClass("active")


			}
		},
		slideNext (index) {
			if (this.currPage < Math.floor((this.content.list.length - 1))) {
				this.currPage++
				$(".dot-list").eq(index).find("li").removeClass("active")
				$(".dot-list").eq(index).find("li").eq(this.currPage).addClass("active")
			}
		},
		evtMouseEnter () {

		},
		evtMouseLeave () {

		}
	}
}
</script>

<style>
.content {
	position: relative;
	float: left;
	width: 296px;
	height: auto;
	margin: 0 0 14px 12px;
	padding-top: 45px;
	background: #fff;
	transition: all 0.3s;
}
.content:hover {
		transform: translateY(-3px);
		box-shadow: 5px 5px 20px #ccc;
		
	}
    .content:hover .slide-pre,.content:hover  .slide-next {
			opacity: 1;
		}
	.content:nth-child(1) {
		margin-left: 0;
	}
	.content .title {
		margin: 0 10px 18px;
		font-size: 16px;
		font-weight: 400;
		text-align: center;
	}
.book {
	border-top: 1px solid #ffac13;
	
}
.book .title {
		color: #ffac13;
	}
	.book .btn-txt {
		color: #ffac13;
		border: 1px solid #ffac13;
		background: #fff;
		
	}
    .book .btn-txt:hover {
			color: #fff;
			background: #ffac13;
		}
	.book .first-desc {
		margin-bottom: 60px; 
	}

.theme {
	border-top: 1px solid #83c44e;
	
}
.theme .title {
    color: #83c44e;
}
.theme .btn-txt {
    color: #83c44e;
    border: 1px solid #83c44e;
    background: #fff;
    
}
.theme .btn-txt:hover {
        color: #fff;
        background: #83c44e;
    }
.game {
	border-top: 1px solid #e53935;
	
}
.game .title {
		color: #e53935;
	}
	.game .btn-txt {
		color: #e53935;
		border: 1px solid #e53935;
		background: #fff;
		
	}
    .game .btn-txt:hover {
			color: #fff;
			background: #e53935;
		}
.app {
	border-top: 1px solid #2196f3;
	
}
.app .title {
    color: #2196f3;
}
.app .btn-txt {
    color: #2196f3;
    border: 1px solid #2196f3;
    background: #fff;
    
}
.app .btn-txt:hover {
        color: #fff;
        background: #2196f3;
    }
.slide-wrap {
	width: 296px;
	height: 340px;
	overflow: hidden;
}

.slide-wrap  .sub-content {
		width: 1200px;
		height: 340px;
		transition: all 0.5s ease;
		
	}

.slide-wrap  .sub-content  .content-item {
	position: relative;
	float: left;
	width: 296px;
	height: 340px;
}

	.slide-wrap  .slide-pre, .slide-next {
		display: block;
		width: 20px;
		height: 46px;
		line-height: 46px;
		font-size: 15px;
		text-align: center;
		margin-top: -24px;
		cursor: pointer;
		z-index: 11;
		background: #b0b0b0;
		color: #fff;
	}
	.slide-wrap  .slide-pre {
		position: absolute;
		left: 0;
		top: 50%;
		opacity: 0;
		transition: all 0.3s;
	}
	.slide-wrap  .slide-next {
		position: absolute;
		right: 0;
		top: 50%;
		opacity: 0;
		transition: all 0.3s;
	}


.subTitle {
	margin: 0 0 10px 0;
	font-weight: normal;
	font-size: 20px;
	text-align: center;
	color: #333;
}
.desc {
	font-size: 12px;
	line-height: 1.5;
	text-align: center;
	color: #b0b0b0;
	width: 200px;
	margin: 0 auto 10px;
}
.content-image {
	display: block;
	width: 216px;
	height: 154px;
	margin: 0 auto;
}
.price {
	font-size: 14px;
	text-align: center;
	color: #333;
}
.btn-txt {
	width: 130px;
	height: 30px;
	line-height: 30px;
	font-size: 12px;
	text-align: center;
	margin: 0 auto;
	margin-bottom: 14px;
	background: #fff;
	cursor: pointer;
}
.btn-list{
	display: block;
	position: absolute;
	
	bottom: 10px;
	width: 296px;
	
	z-index: 11;
	text-align:center;
}
.dot-list {
	margin: 0;
    padding: 0;
    list-style-type: none;

	
}

.dot-list  .dot-item {
		display: inline-block;
    width: 10px;
    height: 10px;
    padding: 10px;
    margin: 0 2px;
    cursor: pointer;
	}

    .dot-list  .dot-item.active .dot {
				background: #fff;
				border: 2px solid #ff6700;
		}
	.dot-list  .dot-item  .dot {
		display: block;
	width: 6px;
	height: 6px;
	border: 2px solid #f5f5f5;
	border-radius: 6px;
	text-align: left;
	text-indent: -9999em;
	overflow: hidden;
	background-color: #b0b0b0;
	transition: all .5s;
	}
      .dot-list  .dot-item  .dot:hover{
		  background-color: #ff6700;
	  }


</style>
