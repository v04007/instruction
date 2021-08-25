// ReflectValue 返回bean的值  
//Golang中的reflect.Indirect()函数用于获取v指向的值，即，如果v是nil指针，则Indirect返回零值。如果v不是指针，则Indirect返回v  
//reflect.ValueOf 来得到接口变量的 Type 和 Value  
//可以通过reflect.Value 轻松得到 reflect.Type 
```
        func ReflectValue(bean interface{}) reflect.Value {  
	   return reflect.Indirect(reflect.ValueOf(bean))  
        }
```

```
	 s2 := []string{"包子", "馒头", "画卷", "螃蟹", "细化"}  
	 t := append(s, make([]string, 5)...)  
	 s3 := append(s2[:2], s2[3:]...)  
```	

```
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
