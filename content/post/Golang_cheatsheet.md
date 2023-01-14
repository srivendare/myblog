---
title: Golang Cheatsheet
categories:
- Golang
date: 2023-01-01
---



2022-03-06

Recently I need to maintain colleague's web scrapers in Golang, here are some notes I took during self-learning, I will keep on updating this article 



1. Lorca  a tool for connect and communicate with web Serber

```go

package main

import (
 "os"
 "os/signal"
 "syscall"

 "github.com/zserge/lorca"
)

func main() {
 var ui lorca.UI 

 ui, _ = lorca.New("https://baidu.com", "", 800, 600, "--display-sync", "--display-translate")

 chSignal := make(chan os.Signal, 1)                      
 signal.Notify(chSignal, syscall.SIGINT, syscall.SIGTERM) 
 select {
 case <-ui.Done():
 case <-chSignal:
 }
 // close ui
 ui.Close()

}
```



The key point of this code block is event listening, 

the `chrome browser` and `ui server` are in different thread, this listener make all process end if there is one process interrupted or terminated

```go
 signal.Notify(chSignal, syscall.SIGINT, syscall.SIGTERM) 
 select {
 case <-ui.Done():
 case <-chSignal:
 }
```

