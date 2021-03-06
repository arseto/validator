# Overview

Simple helper for struct validation using attributes.

# Usage

## Sample Code

```go

type testObject struct {
	ID      int64  `validate:"required"`
	Name    string `validate:"required"`
	Email   string `validate:"required,email"`
	Phone   string `validate:"numeric"`
	Remarks string
}

func ProcessObject(obj *testObject) {
    sv := validator.MakeStructValidator(obj)

    //check if validation failed
    fail := sv.Fail()

    //check if validation success
    //opposite of Fail()
    success := sv.Success()

    //returns error message with detailed field error message
    err := sv.Validate()

    //global error message
    errorMessage := err.Error()

    //field error messages
    fieldErrorMessages := err.Messages()

    //do whatever with error message
    //for http request, return 422 error message
    //etc

    ...
}

```

## Supported validator

* `required`: field value must not equal with its zero value
* `email`: field must be email string
* `numeric`: field must be numeric string

And many more to come next...

# Contributing

Please feel free to submit issue or pull request :).
