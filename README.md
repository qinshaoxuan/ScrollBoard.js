# ScrollBoard.js V 1.0.0

ACM竞赛滚榜展示插件，基于JQuery、Bootstrap

展示页面：[Demo](https://qinshaoxuan.github.io/ScrollBoard/)

按一次回车（可自行指定）可进行一步，即更新一个队的一个未知结果

### V 1.0.0

实现了基本的滚榜展示功能

## 使用方法

### example

```javascript
<script type="text/javascript">
	var board = new Board(
		8, 
		new Array(4, 4, 4), 
		StringToDate("2012-10-13 19:00:00"), 
		StringToDate("2012-10-16 01:00:00")
	);
	board.showInitBoard();
	$('html').keydown(function(e) {
	    if (e.keyCode == 13) {
	            board.keydown();
	    }
	});
</script>
```

由于展示效果需要，请使用空页面添加上面JS代码

`new Board(problemCount, medalCounts, startTime, freezeBoardTime)`

参数依次为题目数、奖牌数数组、比赛开始时间、比赛封榜时间

`Board.showInitBoard()`方法为展示封榜时榜的状态

`Board.keydown()`方法为滚榜时的一步操作，即更新一个队的一个未知结果

### 获取数据

JS文件中的`getSubmitList()`和`getTeamList()`方法分别为获取提交数据和获取队伍数据，请根据后台JSON数据格式自行修改