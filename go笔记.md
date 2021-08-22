// ReflectValue 返回bean的值
//Golang中的reflect.Indirect()函数用于获取v指向的值，即，如果v是nil指针，则Indirect返回零值。如果v不是指针，则Indirect返回v
//reflect.ValueOf 来得到接口变量的 Type 和 Value 
//可以通过reflect.Value 轻松得到 reflect.Type 
##### func ReflectValue(bean interface{}) reflect.Value {
	return reflect.Indirect(reflect.ValueOf(bean))
}
