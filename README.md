# ScrollBoard.js

### V 1.1.0 (2018-12-27)

修复了滚榜中罚时计算的bug

### To be updated

- 对于`waiting`类的展示，以便用于赛时进行实时榜单演示
- 滚榜顺序存在bug等待修复

---

以下为原作者信息

ACM竞赛滚榜展示插件，基于JQuery、Bootstrap

展示页面：[Demo](https://qinshaoxuan.github.io/ScrollBoard.js/)

按一次回车（可自行指定）可进行一步，即更新一个队的一个未知结果

Demo里的数据是西南科技大学第十二届校赛的数据，因为队伍实力差距比较大，可能滚榜的观赏性不强，以后有更好的数据会换掉

### V 1.0.0 (2016-07-02)

实现了基本的滚榜展示功能

## 使用方法

### example
```HTML
<head>
    <link rel="stylesheet" type="text/css" href="bootstrap/css/bootstrap.min.css">
    <link rel="stylesheet" type="text/css" href="css/scrollboard.css">
    <script type="text/javascript" src="js/jquery.min.js"></script>
    <script type="text/javascript" src="bootstrap/js/bootstrap.min.js"></script>
    <script type="text/javascript" src="js/scrollboard.js"></script>
</head>
 
<body>
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
</body>
```

由于展示效果需要，请使用空页面

`new Board(problemCount, medalCounts, startTime, freezeBoardTime)`Borad类构造方法：参数依次为题目数、奖牌数数组（分别为金银铜）、比赛开始时间、比赛封榜时间

`Board.showInitBoard()`方法：展示封榜时榜的状态

`Board.keydown()`方法：滚榜时的一步操作，即更新一个队的一个未知结果

`StringToDate(s)` 方法："yyyy-mm-dd hh:mm:ss"格式字符串转Date对象

### 获取数据

JS文件中的`getSubmitList()`和`getTeamList()`方法分别为获取提交数据和获取队伍数据，请根据后台JSON数据格式自行修改，代码内有详细的注释说明
