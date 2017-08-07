# jQuery动画切换效果jQanimateChange

效果如下：
![](images/img.gif)

allcode：
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>相册切换效果</title>
	<style>
	*{margin: 0px;padding: 0px;}
	li{list-style: none;}
	a{text-decoration: none;}
	body{background: url('images/bg.jpg') no-repeat;height: 100%;width: 100%;}
		ul#pic_con{overflow: hidden;width:750px;height:560px;margin:40px auto;}
		ul#pic_con li{float: left;width:238px;height:169px;margin: 6px;background: #fff;box-shadow: 0 0 20px #fff;border-radius:6px;}
		ul#pic_con li img{width:230px;height:159px;padding:4px;}
		#bg{width: 100%;height: 100%;background: rgba(0,0,0,.4);position: absolute;top: 0px;left: 0px;display: none}

		/*翻页相册*/
		.big_pic{width: 800px;margin: 0 auto;position: relative;}
		.big_pic ul{width:650px;height:450px;margin:40px auto;position: relative;}
		.big_pic ul li{width:650px;height:450px;padding: 5px;position: absolute;top: 0px;left: 0px;}
		.big_pic ul li img{width:650px;height:450px;}
		.big_pic a{display: block;width: 60px;height: 90px;line-height: 90px;text-align: center;position: absolute;font-size: 30px;color: #fff;background: rgba(0,0,0,.5);font-weight: 900;box-shadow: 0 0 15px #fff;border-radius:4px;}
		.big_pic a.prve{top: 50%;margin-top:-45px;left: 0px;}
		.big_pic a.next{top: 50%;margin-top:-45px;right: 0px;}
	</style>
</head>
<body>
	<ul id="pic_con">
		<li><img src="images/main/1.jpg" alt=""></li>
		<li><img src="images/main/2.jpg" alt=""></li>
		<li><img src="images/main/3.jpg" alt=""></li>
		<li><img src="images/main/4.jpg" alt=""></li>
		<li><img src="images/main/5.jpg" alt=""></li>
		<li><img src="images/main/6.jpg" alt=""></li>
		<li><img src="images/main/7.jpg" alt=""></li>
		<li><img src="images/main/8.jpg" alt=""></li>
		<li><img src="images/main/9.jpg" alt=""></li>
	</ul>

	<div id="bg">
		<div class="big_pic">
			<ul>
				<li><img src="images/show/1/1.jpg" alt=""></li>
				<li><img src="images/show/1/2.jpg" alt=""></li>
				<li><img src="images/show/1/3.jpg" alt=""></li>
				<li><img src="images/show/1/4.jpg" alt=""></li>
				<li><img src="images/show/1/5.jpg" alt=""></li>
			</ul>
			<a href="javascript:;" class="prve">&lt;</a>
			<a href="javascript:;" class="next">&gt;</a>
		</div>
	</div>
</body>
</html>
<script  src="js/jquery-1.11.3.js"></script>
<script>
	$(function(){
		$('#pic_con li').click(function(){
			var index =$(this).index();
			for(var p=0;p<5;p++){
				var url = 'images/show/'+index+'/'+(p+1)+'.jpg';
				$('.big_pic li').eq(p).find('img').attr('src',url)
			}
			$('#bg').fadeIn(600);
		});
		//下切换
		$('a.next').click(function(){
			$('.big_pic ul li:last').animate({"left":"100%"},600,function(event){
				$(this).animate({'left':'0'},600);
				$('.big_pic ul').prepend($(this))
			});
			$('.big_pic ul').animate({'left':'-40%'},600);
			$('.big_pic ul').animate({'left':'0'},600);
			event.stopPropagation()
		});
		//上切换
		$('a.prve').click(function(){
			$('.big_pic ul li:last').animate({"left":"-100%"},600,function(event){
				$(this).animate({'left':'0'},600);
				$('.big_pic ul').prepend($(this));
			});
			$('.big_pic ul').animate({'left':'40%'},600);
			$('.big_pic ul').animate({'left':'0'},600);
			event.stopPropagation();
		});
		//点击消失
		$('#bg').click(function(){
			$(this).fadeOut(600);
		})
	})
</script>
```

