# 高级语法

* 初始化
```go
func init() {
    cfg := flag.String("cfg", "", "config path")
    gid := flag.Int("gid", -1, "game id")
    flag.Parse()    
}

func main() {

}
```

*  闭包函数

```go
    func MakeAndSuffix(su string) func(string)string {
        return func(name string) string {
            if !strings.HasSuffix(name, su) {
                return name + su
            }
            return name
        }
    }

    func main() {
        addJpg := MakeAndSuffix(".jpg") 
        addZip := MakeAndSuffix(".zip") 

        log.Printf("%s %s %s %s", addJpg("test"), addZip("a.zip"), addZip("b"), addZip("b.zi"))
    }
```

* 结构对象

```go
    type Player struct {
        Id  int64
        name string
        level int32
        money int64
    }

    type GameData struct {
        bet     int64
        income  int64
        consume int64
    }

    type GamePlayer struct {
        Player      //嵌套
        GameData    //嵌套
        items   map[int64]int64 // 成员
        TableID int32   // 导出成员
        ChairID int32   // 导出成员
    }
```

