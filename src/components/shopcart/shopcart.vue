<template>
	<div class="shopcart">
		<div class="shopcontent">
			<div class="content-left">
				<div class="logo-wrap">
					<div class="logo">
						<span class="shopcartico icon-shopping_cart" ></span>
					</div>
				</div>

				<div class="shopprice">{{totalPrice}}元</div>
				<div class="shopdesc">另需配送费￥{{deliveryPrice}}元</div>
			</div>
			<div class="content-right">
				<div class="pay">
					￥{{minPrice}}元起送
				</div>	

			</div>
		</div>
	</div>

</template>


<script type="text/javascript">
	export default{
		data(){
			return{

			}
		},
		props:{
			deliveryPrice:{
				type:Number
			},
			minPrice:{
				type:Number,
				default:0
			},
			selectFoods:{
				type:Array,
				default(){
					return [{
						price:10,
						count:1
					}]
				}		
			}
		},
		computed:{
			totalPrice(){
			  let total =0;
			  this.selectFoods.forEach((food)=>{
			  		total += food.price *food.count;
			  });
			  return total
 			},
 			totalCount(){
 				let count = 0;
 				this.selectFoods.forEach((food)=>{
 					count+= food.count;
 				})
 			}
		}
	};
</script>


<style type="text/css">
@import '/static/style.css';
	.shopcart{
		position: fixed;
		left: 0;
		bottom: 0;
		z-index: 50;
		width: 100%;
		height: 48px;
		background-color: #000;
	}
	.shopcontent{
		display: flex;
		background-color: #141d27;

	}
	.content-left{
		flex: 1;
	}
	.content-right{
		flex: 0 0 105px;
		width: 105px;
	}
	.logo-wrap{
		position: relative;
		top: -10px;
		margin: 0 12px;
		padding: 6px;
		width: 56px;
		height: 56px;
		display: inline-block;
		border-radius: 50%;
		box-sizing: border-box;
		background-color: #141d27;
	}
	.logo{
		width: 100%;
		height: 100%;
		border-radius: 50%;
		background-color: rgba(0,0,0,0.2);
		text-align: center;
	}
	.shopcartico{
		font-size: 24px;
		color: #80858a;
		line-height: 44px;
	}
	.shopprice{
		display: inline-block;
		vertical-align: top;
		line-height: 24px;
		box-sizing: border-box;
		padding-right: 12px;
		border-right: 1px solid rgba(255,255,255,0.1);
		font-size: 16px;
		font-weight: 700;
		margin-top: 12px;
		color: rgba(255,255,255,0.1);
	}
	.shopdesc{
		display: inline-block;
		line-height: 24px;
		margin: 12px 0 0 12px;
		vertical-align: top;
		color: rgba(255,255,255,0.1);
		font-size: 10px;
	}
	.pay{
		height: 48px;
		line-height: 48px;
		text-align: center;
		font-size: 12px;
		font-weight: 700;
		color: rgba(255,255,255,0.1);
		background-color: #2b333b;
	}
</style>