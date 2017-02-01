1;2802;0cGolang Notes
============

## Mantras

Accept interfaces, return structs

## Miscellaneous 

instruct compiler to ignore file
// +build ignore

list all go projects (note the ellipsis)
$ go list github.com/tcharding/...

run single test function
$ go test -run="Basic" <!-- runs TestBasic() -->

get test coverage
$ go test -cover

and also
$ go test -coverprofile=c.out [-covermode=count]
$ go tool cover -html=c.out <!-- for html view of output -->

$ go test -run=None -bench=Solve -cpuprofile=cpu.out
$ go tool pprof -text -nodecount=20 ./clique.test cpu.out

or -memprofile mem.out
or -blockkprofile block.out

func BenchmarkSolve(b *testing.B) {
    for i := 0; i < b.N; i++ {
        input := "4 2\n0 1\n2 3\n"
        out = new(bytes.Buffer)
        in = bytes.NewBufferString(input)
        solve()
    }
}


