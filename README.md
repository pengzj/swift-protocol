# how to use

```
import (
	"https://github.com/pengzj/swift-protocol"
	"fmt"
)

func main()  {

	in := protocol.Encode(protocol.TYPE_DATA_REQUEST, protocol.MessageEncode(1,1, []byte("hello, this is first message from client")))

	fmt.Println(in)

	length := protocol.GetBodyLength(in)

	fmt.Println(length)

	packateType, data := protocol.Decode(in)

	msgId, routeId, body := protocol.MessageDecode(data)

	fmt.Println(packateType, data)
	fmt.Println(msgId, routeId, string(body))
}
```

# benchmark
```
go test -bench=.
goos: darwin
goarch: amd64
BenchmarkMessageEncode-4        20000000                58.4 ns/op
BenchmarkMessageDecode-4        100000000               17.1 ns/op
BenchmarkEncode-4               20000000               100 ns/op
BenchmarkDecode-4               100000000               10.8 ns/op
PASS

```
