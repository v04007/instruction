```
        for _, key := range keyArr {
            d, err = PostCoin(key)
            if err != nil {
             continue
         }
         return d,err
        }
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

```
        //结构体快速赋值
	type Point struct {
		X, Y float64
	}

	type ColoredPoint struct {
		Point
		Color string
	}

	var cp ColoredPoint
	cp.X = 11
	fmt.Println(cp) //{{11 0} }
```

```
//求余、goto用法
	if d, err = postCoin(keyArr[currentKey]);d.Status!=0 {
		previousKey:=currentKey
			if d.Status.ErrorCode== ErrorCode  {
				next:
				currentKey = (currentKey + 1) % len(keyArr)
				if currentKey!=previousKey {
					if d, err = postCoin(keyArr[currentKey]);d.Status== ErrorCode  {
						goto next
					}
					}else{
						logger.LogError(err.Error())
					}
			}
	}
	return
```

```
###gin处理跨域
package main

import (
	"time"

	"github.com/gin-contrib/cors"
	"github.com/gin-gonic/gin"
)

func LoginAdmin(c *gin.Context) {
	c.JSON(200, gin.H{
		"message": "Hello 登录成功!",
	})
}

func main() {
	router := gin.Default()
	/*
	   cors.New方法返回一个函数参数是c *gin.Context
	   将这个参数赋值给mwCORS,直接当中间间使用,
	   默认修改返回的请求头,实现跨域功能
	   cors.Config为一个结构体,结构体实例后传入cors.New实现生成中间件功能
	*/
	mwCORS := cors.New(cors.Config{
		//准许跨域请求网站,多个使用,分开,限制使用*
		AllowOrigins: []string{"http://localhost:9528"},
		//准许使用的请求方式
		AllowMethods: []string{"PUT", "PATCH", "POST", "GET", "DELETE"},
		//准许使用的请求表头
		AllowHeaders: []string{"Origin", "Authorization", "Content-Type"},
		//显示的请求表头
		ExposeHeaders: []string{"Content-Type"},
		//凭证共享,确定共享
		AllowCredentials: true,
		//容许跨域的原点网站,可以直接return true就万事大吉了
		AllowOriginFunc: func(origin string) bool {
			return true
		},
		//超时时间设定
		MaxAge: 24 * time.Hour,
	})
	router.Use(mwCORS)
	router.POST("login", LoginAdmin) //管理后台登陆
	router.Run("localhost:8080")
}
```
