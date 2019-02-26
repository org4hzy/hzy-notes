# 深复制

* golang 按值传递参数，正常赋值都是值拷贝，但如果类型里面有指针，也是指针的值拷贝，此时就有两个变量指向同一块内存了。

```go
    // 注意： range时v的值为同一块内存！引用内存是需要格外小心。
    func test() {
        type A struct {
		    aa  int32
	    	txt string
    	}

        ta := []A {
            {aa:1, txt:"test 1"},
            {aa:2, txt:"test 2"},
        }

        for k, v := range ta {
            //遍历的时候，v的地址指向同一块内存!
            log.Printf("%d v = %p %v", k, &v, v)
        }
    }
```
```text
output :
2019/02/26 10:18:14 0 v = 0xc042003020 {1 test 1}
2019/02/26 10:18:14 1 v = 0xc042003020 {2 test 2}
```

``` go
//deep copy 序列化和反序列化可以达到深度拷贝的效果
func DeepCopy(des interface{}, src interface{}) error {
    if des == nil || src == nil {
        return fmt.Errorf("params is nil")
    } 

    bytes, err := json.Marshal(src)
    if err != nil {
        return err
    }
    return json.Unmarshal(bytes, des)
}
```


