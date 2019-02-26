# ????

* ??
```go
func init() {
    cfg := flag.String("cfg", "", "config path")
    gid := flag.Int("gid", -1, "game id")
    flag.Parse()    
}

func main() {

}
```

* ??
?Go?????????????(????)
```go
    // ????
    func MakeAndSuffix(su string) func(string)string {
        return func(name string) string {
            if !strings.HasSuffix(name, su) {
                return name + su
            }
            return name
        }
    }

    func main() {
        // ????
        addJpg := MakeAndSuffix(".jpg") //..????
        addZip := MakeAndSuffix(".zip") //..????

        log.Printf("%s %s %s %s", addJpg("test"), addZip("a.zip"), addZip("b"), addZip("b.zi"))
    }
```

* ??/??? 

```go
    //?????????????
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
        Player      //??
        GameData    //??
        items   map[int64]int64 //??
        TableID int32   //??
        ChairID int32   //??
    }

```

* ??

