# 2019-02-22 周报

* 百家乐bug
```text
1.后台统计问题:  玩家登录了游戏，但进桌失败后，没有释放掉玩家，这个数据会发给后台显示。
2.2号桌子人数显示异常问题:人数字段是独立的，异常原因未知。现在加上校验(该字段和实际人数的校验，并修正)。

```
## 对于同类功能性函数，设计相对稳定的参数布局。便于检测参数和实现功能。

原代码设计
```go
// keepCnt [0,5], 越界为-1 ？
func (t *Table)init() {
    t.keepCnt = 0 
}

func (t *Table)ThrowInto(player *gplayer.Player) {
    //throw into success ...
    t.keepCnt++
    // do other things ...
}

func (t *Table)ThrowOff(player *gplayer.Player) {
    //throw off check success ...
    t.keepCnt--
    // do other things...
}
```
