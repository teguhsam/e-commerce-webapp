# ecommerce-webapp

Work-In-Progress
eCommerce Web App with Golang

# Requirements

```
brew install make
brew install mariadb
```

1. go
2. make
3. mariadb
4. bootstrap (https://getbootstrap.com)

## Go Packages

Stripe API

```
go get -u github.com/stripe/stripe-go/v72
```

# To run application

```
go run ./cmd/web
```

# Future Improvements:

1. Allow macOS to trust build, so it does not have to ask for connection permission each time the application is run
