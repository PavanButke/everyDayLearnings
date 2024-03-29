# 10th Of Feb 24

## Viper in Golang
- Viper is a popular configuration management library in Go.
- It helps manage application configuration settings from various sources like JSON, YAML, environment variables, etc.
- Features include multiple sources, automatic type conversion, default values, hierarchical configuration, and watching/reloading configurations.

## ContextKey in Go
- `ContextKey` is typically used in Go's `context` package for identifying and retrieving context values.
- It's a custom type used as keys when associating values with a context using `context.WithValue()`.

## iota in Go
- `iota` is a predeclared identifier in Go used in const declarations to simplify constant increments.
- It generates sequential values starting from 0 and incrementing by 1 for each subsequent const declaration in the group.
- ==> @Generate in Java

## GPClient
- `GPClient` could refer to a client implementation in Go for interacting with a specific service or API.
- "GP" might stand for "General Purpose" or represent the initials of a particular service or product.
- The `GPClient` would typically be a struct or package designed for communication with the remote service. 
- ==> repository class in java

## Slices
- []struct_name

## Pointers
- * -> gets value
- & -> get mem address

## claims
- Associated with JWT
- e payload of the JWT,

## jwt with go
- token,err := jwt.NewWithClaims(jwt.SigningMethodHS256 , claims).SignedString([]byte(SECRET_KEY)
  
## bson
- 
BSON, which stands for Binary JSON (JavaScript Object Notation), is a binary-encoded serialization of JSON-like documents. It's designed to be lightweight, traversable, and efficient in both storage and data exchange.

` \x1E\x00\x00\x00                        // Total document size: 30 bytes
\x02                                     // String type
name\x00                                 // Field name: "name"
\x09\x00\x00\x00John Doe\x00             // String value: "John Doe"`

## context package
- The Context package in Go provides a way to pass request-scoped values, cancellation signals, and deadlines across API boundaries and between goroutines.

package main

import (
	"context"
	"fmt"
	"time"
)

`func main() {
	// Create a new empty context
	parentCtx := context.Background()

	// Create a child context with a cancellation signal after 1 second
	childCtx, cancel := context.WithTimeout(parentCtx, time.Second)

	// Ensure the cancel function is called to release resources when finished
	defer cancel()

	// Use the child context or pass it to functions that support it
	fmt.Println("Child Context:", childCtx)
}`

## Generate New Object ID
- user.ID = primitive.NewObjectID()
