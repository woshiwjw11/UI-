<template>
  <div>
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
  						<span class="title">服务态度</span>
  						<star :size="36" :score="seller.foodScore"></star>
  					</div>
  					<div class="score-wrapper">
  						<span class="title">服务态度</span>
  						<star :size="36" :score="seller.foodScore"></star>
  					</div>
  				</div>
  			</div>
  			<split></split>
  		</div>
  	</div>
  </div>
</template>
<script type="text/ecmascript-6">
  export default{

  };
</script>
<style lang="stylus" rel="stylesheet/stylus">
</style>
