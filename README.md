## Terminal progress bar for Go  

Simple progress bar for console programms. 
    

### Installation
```
go get github.com/cheggaaa/pb
```   

### Usage   
```Go
package main

import (
	"github.com/cheggaaa/pb"
	"time"
)

func main() {
	count := 100000
	bar := pb.StartNew(count)
	for i := 0; i < count; i++ {
		bar.Increment()
		time.Sleep(time.Millisecond)
	}
	bar.FinishPrint("The End!")
}
```   
Result will be like this:
```
> go run test.go
37158 / 100000 [================>_______________________________] 37.16% 1m11s
```


More functions?  
```Go  
// create bar
bar := pb.New(count)

// refresh info every second (default 200ms)
bar.RefreshRate = time.Second

// show percents (by default already true)
bar.ShowPercent = true

// show bar (by default already true)
bar.ShowBar = true

// no need counters
bar.ShowCounters = false

// show "time left"
bar.ShowTimeLeft = true

// show average speed    
bar.ShowSpeed = true

// convert output to readable format (like KB, MB)     
bar.Units = pb.U_BYTES

// and start
bar.Start()
``` 

Want handle progress of io operations?    
```Go
// create and start bar
bar := pb.New(myDataLen)
// for output like MB, KB
bar.Units = pb.U_BYTES
bar.Start()

// my io.Reader
r := myReader

// my io.Writer
w := myWriter

// create multi writer
writer := io.MultiWriter(w, bar)

// and copy
io.Copy(writer, r)

// show example/copy/copy.go for advanced example

```

Not like the looks?
```Go
// insert before usage
pb.BarStart = "<"
pb.BarEnd   = ">"
pb.Empty    = " "
pb.Current  = "-"
pb.CurrentN = "."
```
