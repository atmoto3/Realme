<template>
	<div style='position: relative;padding-left:2.16rem;'>
		<!-- 左侧边栏 -->
		<div class='sidebarClass'>
			<van-sidebar v-model="sidebarKey" @change="onChangeSidebar">
				<van-sidebar-item
					v-for="(n, inx) in sidebar_arr"
					:title="n.txt"
					:key="inx" />
			</van-sidebar>
		</div>

		<!-- 右侧商品区 -->
		<div class='sidebarGoods'>
			<img src='@/assets/1.jpg'></img>
			<div class='goodsItem' 
				v-for='(n, inx) in goodsListObj'
				@click="gotoGoodsBuy(n)">
				<img :src="n.goods_img" />
				<p> {{n.goods_name}} </p>
				<b> {{n.goods_price}} </b>
			</div>
		</div>

		<footer_bar></footer_bar>
	</div>
</template>

<script>
import footer_bar from './footer_bar'
import axios from 'axios'

export default{
	name:'cateList',
	data(){
		return {
			msg:'栏目页面',
			sidebarKey:0,
			sidebar_arr:[
				{
					txt:'新品快报'
				},{
					txt:'GT系列'
				},{
					txt:'Q系列'
				}
				,{
					txt:'V系列'
				},{
					txt:'X系列'
				},{
					txt:'耳机'
				},{
					txt:'智能手表'
				},{
					txt:'电脑办公'
				},{
					txt:'充电'
				},{
					txt:'箱包潮服'
				},{
					txt:'家居个护'
				}
			],
			goodsListObj:null
		}
	},
	components:{footer_bar},
	created(){
		axios.get('http://localhost:3344/cate_goods_list_0')
				.then(_d=>{
					// console.log( _d.data );
					this.goodsListObj = _d.data;
				});
	},
	methods:{
		// 切换产品列表
		onChangeSidebar( _inx ){
			// console.log( _inx );
			axios.get('http://localhost:3344/cate_goods_list_' + _inx)
				.then(_d=>{
					// console.log( _d.data );
					this.goodsListObj = _d.data;
				})
		},
		gotoGoodsBuy( _n ){
			console.log( _n )
			// this.$router.push('/goods_detail');
			this.$router.push({
				name:'goods_detail',
				params:{goodsInfo:_n}
			});
		}
	}
}
</script>

<style scoped>
.sidebarClass{
	position: fixed;left: 0;top: 0;
}


/* 右侧商品 */
.sidebarGoods img{
	border-radius:.3rem;
	
}


.goodsItem{
	float: left;width: 44%;
	margin: 0rem 0.2rem 0.44rem 0.2rem;
	font-size: .37333rem;overflow: hidden;
}



.goodsItem b{color:#f00;}


</style>