1. Conclusion and further discussion  
1.1 Precision and soundness
	Soundness and precision are 2 properties used to measure static analysis tools.
	
	A static analysis tool is sound, if for a specific property to check, it finds all of its occurences in the code. In other words, the less false negatives the static tool has, the more sound it is.

	Given the following program:
	```
	r := 1
	if rand.Int() > 0.5 {
		r = 2
	}
	```
	An unsound analysis will result in `r=1` ignoring the possible value of `2` where as a sound analysis will result in `r=1` or `r=2`.

	Precision is the ability of a static analysis tool to flag only the property we're interested at. As previously, the less false positives, the more the tool is precise.
	If we return the example from above, an imprecise analysis might say `r` is between `0` and `100` where a precise analysis will say `r` is only `1` or `2`.

	Precision and Soundness are tradeoff. Having the ability to flag more cases makes the program more sound, but might result in false positives. On the other way around, limiting the number of cases to cover makes the analysis more precise.

1.2 Other tools
There are of course the built-in tools such as `go vet` `go imports` and `go fmt`

`go fmt` - Gofmt formats Go programs. It uses tabs for indentation and blanks for alignment. Alignment assumes that an editor is using a fixed-width font.
`go vet` - Vet examines Go source code and reports suspicious constructs, such as Printf calls whose arguments do not align with the format string
`go imports` - The command go imports updates your Go import lines, adding missing ones and removing unreferenced ones.

There's also an awesome [list](https://github.com/golangci/awesome-go-linters) of go analysis tools from the go community. It contains tools from different categories you can integrate into to your toolchain. 
	
[staticcheck](https://github.com/dominikh/go-tools) and [golanglint-ci](https://github.com/golangci/golangci-lint) are some of the more noteable tools. 
staticcheck is similar to `go vet` but applies many more checks such as forgetting to `unlock` a `mutex` using  the defer statement, validating json tags correctness and so on.

golanglint-ci is a fast Go linters runner. It runs linters in parallel, uses caching, supports `yaml` config, has integrations with all major IDE and has dozens of linters included. You can look at the full list of linters [here](https://golangci-lint.run/usage/linters/).

1.3 Further reading:
https://github.com/golang/example/tree/master/gotypes - A deeper dive into the topics we talked about in the AST part. 
https://www.youtube.com/watch?v=uTMvKVma5ms&ab_channel=GopherAcademy -A deeper dive into SSA 

1.4 Dicussion
	Any questions?