# gohunter

[![Tests](https://github.com/solar-jsoc/gohunter/workflows/Tests/badge.svg)](https://github.com/solar-jsoc/gohunter/actions)
[![Coverage Status](https://coveralls.io/repos/github/solar-jsoc/gohunter/badge.svg?branch=master)](https://coveralls.io/github/solar-jsoc/gohunter?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/solar-jsoc/gohunter)](https://goreportcard.com/report/github.com/solar-jsoc/gohunter)
[![PkgGoDev](https://pkg.go.dev/badge/github.com/solar-jsoc/gohunter)](https://pkg.go.dev/github.com/solar-jsoc/gohunter)


Client library for [hunter.io](https://hunter.io)

# Methods

Supported methods:

- [x] GET domain-search
- [x] GET email-finder
- [x] GET email-verifier
- [x] GET email-count
- [x] GET account
- [ ] GET leads (get all leads)
- [ ] GET lead/{number} (get one lead)
- [ ] POST leads (create lead)
- [ ] PUT lead/{number} (update lead)
- [ ] DELETE lead/{number} (delete lead)

# Installation

```
    go get github.com/solar-jsoc/gohunter
```

# Examples

- client init:
 
    ```go
    client := gohunter.NewClient("token", gohunter.WithCustomClient(http.DefaultClient))
    ```
    
- domain-search
    
    ```go
    result, err := client.DomainSearch(context.TODO(), "intercom.io", "intercom", 
    	gohunter.WithLimit(20), 
    	gohunter.WithDepartment(DepartmentIT, DepartmentFinance), 
    	gohunter.WithSeniority(SenioritySenior),
    	gohunter.WithEmailType(EmailTypePersonal),
    	gohunter.WithOffset(10))
    if err != nil {
        ...
    }
    ```
    	
- email-finder

    ```go
  	result, err := client.FindEmail(context.TODO(), "intercom.io", "intercom", gohunter.UsingFullName("John Doe"))
  	if err != nil {
  		...
  	}
    ```

- email-verifier
    
    ```go
  	result, err := client.VerifyEmail(context.TODO(), "ciaran@intercom.io")
  	if err != nil {
  		...
  	}
    ```
  
- email-count
    
    ```go
  	result, err := client.EmailCount(context.TODO(), "", "intercom", gohunter.EmailTypePersonal)
  	if err != nil {
  		...
  	}
    ```
  
- account
    
    ```go
    result, err := client.AccountInformation(context.TODO())
    if err != nil {
    	...
    }
    ```
