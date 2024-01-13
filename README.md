### Forked from [modelfoxdotdev/modelfox-go](https://github.com/modelfoxdotdev/modelfox-go)
_Many thanks for such tool_

# Purpose of fork
Fixed bug with path (directory names not same as in `CFLAGS` and `LDFLAGS`)  
I am not sure how this bug could appear in original repo.
I tried to contact with dev - no result for now.
I'll update this readme when I get some info or the bug in original repo is fixed

# ModelFox for Go

- [Watch the Video](https://www.modelfox.dev)
- [Read the Docs](https://www.modelfox.dev/docs)

The ModelFox Go module makes it easy to make predictions with your ModelFox machine learning model from Go.

## Usage

```
$ go get -u github.com/TimaSlipko/modelfox-go
```

```go
import "github.com/TimaSlipko/modelfox-go"

model, _ := modelfox.LoadModelFromPath("./heart_disease.modelfox", nil)
defer model.Destroy()

input := modelfox.PredictInput{
  "age":    63,
  "gender": "male",
  // ...
}

output := model.PredictOne(input, nil)

fmt.Println("Output:", output.ClassName)
```

For more information, [read the docs](https://www.modelfox.dev/docs).

## Platform Support

ModelFox for Go is currently supported on the following combinations of `$GOARCH` and `$GOOS`:

- `amd64` `linux`
- `arm64` `linux`
- `amd64` `darwin`
- `arm64` `darwin`
- `amd64` `windows`

ModelFox for Go links to the modelfox C library, so cgo is required. The modelfox C library will be linked statically into your executable, so when you run `go build` you will still get a statically linked executable you can run anywhere without having to worry about dynamic linking errors.