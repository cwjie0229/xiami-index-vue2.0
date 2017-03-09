<template>
  <header class="top-container">
		<div class="top-bar clearfix">
			<div class="topbar-nav">
				<ul class="nav-wrap">
					<li v-for="(item,index) in navs" class="nav clearfix">
                        <a :href="item.sourceUrl" class="nav-name" target="_blank">{{item.name}}</a>
                        <span class="nav-separate" v-show="index !== 8">|</span>
					</li>
				</ul>
			</div>
			 <div class="topbar-info">
				<a href="http://order.mi.com/site/login?redirectUrl=http://www.mi.com/index.html">登陆</a>
				<span class="nav-separate">|</span>
				<a href="https://account.xiaomi.com/pass/register">注册</a>
			</div>
			 <div class="topbar-cart fa cart-arrow-down"  @mouseenter="evtCartEnter"   @mouseleave="evtCartOut">
				<div class="cart"  :class="{'active': cartStatus}">
                    <i class="fa fa-cart-arrow-down icon-cart"></i>
					<a href="http://static.mi.com/cart/"> 购物车( <span>0</span>)
						</a>
				</div>
				<div class="cart-list"  transition="fadein"  v-show="cartStatus">
					购物车中还没有商品，赶快选购吧！
				</div>
			</div>

		</div>
  </header>
</template>
<script>
export default {
	data () {
		return {
			navs: [
				{name: '小米商城', sourceUrl: 'http://www.mi.com/index.html'},
				{name: 'MIUI', sourceUrl: 'http://www.miui.com/'},
				{name: '米聊', sourceUrl: 'http://www.miliao.com/'},
				{name: '游戏', sourceUrl: 'http://game.xiaomi.com/'},
				{name: '多看阅读', sourceUrl: 'http://www.duokan.com/'},
				{name: '云服务', sourceUrl: 'https://i.mi.com/'},
				{name: '小米网移动版', sourceUrl: 'http://www.mi.com/c/appdownload/'},
				{name: '问题反馈', sourceUrl: 'http://static.mi.com/feedback/'},
				{name: 'Select Region', sourceUrl: 'http://www.mi.com/index.html'}
			],
			timer: '',
			cartStatus: false
		}
	},
 	mounted:function(){
        
    },
	methods: {
		evtCartEnter: function () {
      this.cartStatus = true
      clearInterval(this.timer)
		},
    evtCartOut: function () {
      let self = this
      this.timer = setTimeout(function () {
        self.cartStatus = false
      }, 300)
    }
	},
	components: {
	}

}
</script>
<style scoped>
.top-container {
	width: 100%;
	height: 40px;
	background: #333;
}
.top-bar {
	position: relative;
	width: 1226px;
	margin: 0 auto;
	font-size: 12px;
  z-index: 11;
}
.topbar-nav {
	float: left;
	display: inline-block;
	height: 40px;
	line-height: 40px;
	overflow: hidden;
}

.nav-wrap {
	display: inline-block;
	margin: 0;
	padding: 0;
	list-style: none;
	
}
.nav-wrap  .nav {
    display: inline-block;
    text-decoration: none;
    height: 40px;
    line-height: 40px;
    padding-left: 5px;
}
.nav-wrap  .nav .nav-name:hover{
    color: #fff;
}
.nav-wrap  .nav .nav-name {
    display: inline-block;
    font-size: 12px;
    color: #b0b0b0;
    text-decoration: none;
}
.nav-wrap  .nav	.nav-separate {
    display: inline-block;
    color: #b0b0b0;
    margin-left: 5px;
}
.topbar-info {
position: absolute;
top: 0;
right: 140px;
height: 40px;
line-height: 40px;


}
.topbar-info  a {
    color: #b0b0b0;
    text-decoration: none;
}
.topbar-info a:hover {
    color: #fff;

}
.topbar-info aspan {
    color: #b0b0b0;
}
.topbar-cart {
	position: relative;
	float: right;
	width: 120px;
	background: #424242;
	height: 40px;
	line-height: 40px;
	cursor: pointer;
    
  }
  .topbar-cart:hover {
    background: #fff;
  }
	  .topbar-cart a, .icon-cart, span {
      color: #ff6700;
    }
.topbar-cart	.active {
		background: #fff;
   
	}
.topbar-cart	.active a {
      color: #ff6700;
    }
 .topbar-cart   .active span {
      color: #ff6700;
    }
.topbar-cart	a {
		display: block;
		width: 100%;
		height: 100%;
		padding-left: 40px;
		color: #b0b0b0;
		text-decoration: none;
		box-sizing: border-box;
	}
.topbar-cart	span {
		color: #b0b0b0;
	}
 .topbar-cart .icon-cart {
    position: absolute;
    left: 15px;
    top: 10px;
    color: #b0b0b0;
    font-size: 20px;
  }
  .cart-list {
	position: absolute;
	right: 0;
	top: 39px;
  width: 316px;
  height: 96px;
  line-height: 96px;
	text-align: center;
	color: #b0b0b0;
	background: #fff;
	box-shadow: 0 0 5px #ccc;
  z-index: 10;
  overflow: hidden;
}

.fadein-transition {
  transition: all .5s ease;
  height: 96px;
}

.fadein-enter, .fadein-leave {
  height: 0;
}
</style>
