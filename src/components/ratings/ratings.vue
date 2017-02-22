<template>
  	<div class="ratings">
  		<div class="ratings-content">
  			<div class="overview">
  				<div class="overview-left">
  					<h1 class="score"></h1>
  					<div class="title">综合评分</div>
  					<div class="rank"></div>
  				</div>
  				<div class="overview-right">
  					<div class="score-wrapper">
  						<span class="title">服务态度</span>
  						<star :size="36" :score="seller.foodScore"></star>
  					</div>
  					<div class="score-wrapper">
  						<span class="title">商品评分</span>
  						<star :size="36" :score="seller.foodScore"></star>
  					</div>
  					<div class="score-wrapper">
  						<span class="title">送达时间</span>
  						<span class="delivery">{{seller.deliveryTime}}分钟</span>
  					</div>
  				</div>
  			</div>
  			<split></split>
  			<ratingselect :select-type="selectType" :only-content="only-contentContent" :desc="desc" :ratings="ratings"></ratingselect>
  			<div class="rating-wrapper">
		        <ul>
		          <li v-for="rating in ratings" v-show="needShow(rating.rateType, rating.text)" class="rating-item">
		            <div class="avatar">
		              <img width="28" height="28" :src="rating.avatar">
		            </div>
		            <div class="content">
		              <h1 class="name">{{rating.username}}</h1>
		              <div class="star-wrapper">
		                <star :size="24" :score="rating.score"></star>
		                <span class="delivery" v-show="rating.deliveryTime">{{rating.deliveryTime}}</span>
		              </div>
		              <p class="text">{{rating.text}}</p>
		              <div class="recommend" v-show="rating.recommend && rating.recommend.length">
		                <span class="icon-thumb_up"></span>
		                <span class="item" v-for="item in rating.recommend">{{item}}</span>
		              </div>
		              <div class="time">
		                {{rating.rateTime | formatDate}}
		              </div>
		            </div>
		          </li>
		        </ul>
      		</div>
  		</div>
  	</div>
</template>
<script type="text/ecmascript-6">
import star from 'components/star/star';
import BScroll from 'better-scroll';
  export default{
  	props: {
  		seller: {
  			type: Object
  		}
  	},
  	created() {
  		this.$http.get('/api/ratings').then((response) => {
        response = response.body;
        if (response.errno === 0) {
          this.ratings = response.data;
          this.$nextTick(() => {
            this.scroll = new BScroll(this.$els.ratings, {
              click: true
            });
          });
        }
      });
  	},
  	components: {
  		star
  	}
  };
</script>
<style lang="stylus" rel="stylesheet/stylus">
	.ratings
		position:absolute
		top:174px
		bottom:0
		left:0
		width:100%
		overflow:hidden
		.overview
			display:flex
			padding:18px 0
			.overview-left
				flex:0 0 137px
				padding:6px 0
				width:137px
				text-align:center
				@media only screen and (max-width:320px)
					flex:0 0 120px
					width:120px
					.score
						marign-bottom:6px
						line-height:28px
						font-size:24px
					.title
						marigin-bottom:8px
						line-height:12px
						font-size:12px
						color:rgb(7,17,27)
					.rank
						line-height:10px
						font-size:10px
						color:rgb(147,153,159)
				.overview-right
					flex:1
					padding:6px 0 6px 24px
					@media only screen and (max-width:320px)
						padding-left:6px
						.score-wrapper
							marigin-bottom:8px
							font-size:0
							.title
								display:inline-block
</style>
