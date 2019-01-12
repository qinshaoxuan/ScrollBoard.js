# ScrollBoard.js

（我的）展示页面：[Demo](https://xzm2000.github.io/ScrollBoard.js/)

### 20190112 bug fix：

- 对于0题选手固定排位顺序，防止跳来跳去
- 对于直接读cf数据改成了倒序读入，遇到赛后提交直接break

### 在原作者的基础上修改了以下内容

- 修改滚榜的时候翻题顺序是从左往右
- 修复总罚时按秒计算的bug（改为每个题的分钟数的加和）
- 让CE不计入罚时
- 对于实时当做外榜的应用场景，对于`Waiting`的评测结果也予以展示（由于没有实际应用，不知道是否存在bug）
- 增加打星队的相关处理
- 因为本人的应用场景的cf gym比赛的滚榜相关，所以js加了一段hexSha512的计算，然后在获取的时候调用的cf的API接口
- 对于同罚时的情况，第三关键字改为按照last AC submit id排序
- 增加了一血标识
- 为了防止榜单显示错误，自动把用户名中的`.`改为`_`

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
