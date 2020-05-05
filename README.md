# Filego

Filego is a simple Golang wrapper around Gofile.io's API. It provides a basic library for uploading files inside your code and an executable to quickly upload files to Gofile.

# Documentation

Here is a basic example for uploading a file with email and password:

```go
package main

import (
	"fmt"
	"github.com/0xSteeW/filego"
	"os"
)

func main() {
	conn, err := filego.NewConnection()
	if err != nil {
		fmt.Println(err.Error())
		return
	}
	uploadStruct := &filego.Connection{Email: "example@email.com", Password: "rockyou"}
	conn.Construct(uploadStruct)
	// Open a file for uploading
	reader, _ := os.Open("test.file")
	conn.AddFile("testfilename", reader)
	response, err := conn.Upload()
	if err != nil {
		fmt.Println(err.Error())
		return
	}
	fmt.Println(response.Data["code"])
	
}
```
