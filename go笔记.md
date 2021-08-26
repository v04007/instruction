```
        //for _, key := range keyArr {
        //    d, err = PostCoin(key)
        //    if err != nil {
        //     continue
        // }
        // return d,err
        //}
```
```       
         //append 截取
	 s2 := []string{"包子", "馒头", "画卷", "螃蟹", "细化"}  
	 t := append(s, make([]string, 5)...)  
	 s3 := append(s2[:2], s2[3:]...)  
```	

```
        //for 循环指针赋值为同一个解决方法
	s := []string{"红烧肉", "清蒸鱼", "溜达下", "蒸螃蟹", "鲍鱼粥"}
	s2 := make([]*string, len(s))

	for i, v := range s {
		s2[i] = &v
	}
	fmt.Println(s[0])
	fmt.Println(*s2[0], *s2[1])
	// 	红烧肉
	// 鲍鱼粥 鲍鱼粥

	for i, _ := range s {
		s2[i] = &s[i]
	}
	fmt.Println(s[0])
	fmt.Println(*s2[0], *s2[1])
	// 	红烧肉
	// 红烧肉 清蒸鱼
```

```
        //xorm in 查询
	type Users struct {
		Id   int64
		Name string `xorm:"varchar(25) [not ]null unique 'usr_name' comment('姓名')"`
	}
	var U []Users
	engine.In("id", []int{1, 2, 3}).Find(&U)
	fmt.Println(&U)
```

```   
        //break语句还可以在语句后面添加标签，表示退出某个标签对应的代码块
	BREAKDEMO1:
		for i := 0; i < 10; i++ {
			for j := 0; j < 10; j++ {
				if j == 2 {
					break BREAKDEMO1
				}
				fmt.Printf("%v-%v\n", i, j)
			}
		}
		fmt.Println("...")
	}
```

```
        //goto语句通过标签进行代码间的无条件跳转。goto语句可以在快速跳出循环、避免重复退出上有一定的帮助。
	//Go语言中使用goto语句能简化一些代码的实现过程。 例如双层嵌套的for循环要退出时
	for i := 0; i < 10; i++ {
		for j := 0; j < 10; j++ {
			if j == 2 {
				// 设置退出标签
				goto breakTag
			}
			fmt.Printf("%v-%v\n", i, j)
		}
	}
	return
breakTag:
```
