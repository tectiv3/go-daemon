# go-daemon [![Build Status](https://travis-ci.org/sevlyar/go-daemon.png?branch=master)](https://travis-ci.org/sevlyar/go-daemon) [![GoDoc](https://godoc.org/github.com/sevlyar/go-daemon?status.png)](https://godoc.org/github.com/sevlyar/go-daemon)
 
Library for writing system daemons in Go.

## Features
* Goroutine-safe daemonization
* Out of box a work with a pid-file and log-file
* Easy handling of system signals
* The control of a daemon

## Installation

	go get github.com/sevlyar/go-daemon

## How it works

```go
func main() {
	Pre()

	context := new(Context)
	child, _ := context.Reborn()

	if child != nil {
		PostParent()
	} else {
		defer context.Release()
		PostChild()
	}
}
```

![](img/idea.png)

## History

### 14.01.12
* released new version, old version moved to github.com/sevlyar/go-daemon/oldapi
