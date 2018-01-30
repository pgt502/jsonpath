[![Build Status](https://travis-ci.org/cthulhu/jsonpath.svg?branch=master)](https://travis-ci.org/cthulhu/jsonpath)  [![Goreport](https://goreportcard.com/badge/github.com/cthulhu/jsonpath)](https://goreportcard.com/badge/github.com/cthulhu/jsonpath) [![License MIT](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/cthulhu/jsonpath/master/LICENSE)


# jsonpath - Json generation by dot notation

This library is very close to [mongodb's dot notation](https://docs.mongodb.com/manual/core/document/#dot-notation) with a bit of extensions.

Supported syntaxes

|input hash value | output json result      |
|-----------------|-------------------------|
|{"0.value":"100"}| [{"value":"100"}]       |
|{"1.value":"100"}| [null, {"value":"100"}] |
|{"value":"100"}  |  {"value":"100"}        |
|{"value.1":"100"}|  {"value":[null, "100"]}|
|{"v.0.k":"100"}  |  {"v":[{"k":100}]}      |
|{"v.[]":"1,2,3"}  |  {"v":["1","2","3"]}      |

# Benchmarks

Run benchmarks

    go test -bench=.

Results

V0.0.1

    BenchmarkComplexJSONPathArray-8      	  100000	     13557 ns/op
    BenchmarkSimpleJSONPathArrayWithNum-8	  500000	      3237 ns/op
    BenchmarkSimpleJSONPathSimple-8      	 1000000	      1940 ns/op
    BenchmarkJSONNative-8                	 1000000	      1087 ns/op

v0.0.2

    BenchmarkComplexJSONPathArray-8             	  100000	     13248 ns/op
    BenchmarkSimpleJSONPathArrayWithNum-8       	  500000	      2799 ns/op
    BenchmarkSimpleJSONPathArrayInsideArray-8   	  500000	      3308 ns/op
    BenchmarkSimpleJSONPathArrays-8             	  500000	      2830 ns/op
    BenchmarkSimpleJSONPathSimple-8             	 1000000	      1722 ns/op
    BenchmarkJSONNative-8                       	 1000000	      1014 ns/op

# Installation

go get github.com/cthulhu/jsonpath

# Usage

    in := map[string]string{"0.value": "100.00"}
    jsobBytes := jsonpath.Marshal(in)

For more examples check jsonpath_test.go file

# LICENSE

See LICENSE file
