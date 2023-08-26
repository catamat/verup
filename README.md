# Verup
[![License](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/catamat/verup/blob/master/LICENSE)
[![Build Status](https://travis-ci.org/catamat/verup.svg?branch=master)](https://travis-ci.org/catamat/verup)
[![Go Report Card](https://goreportcard.com/badge/github.com/catamat/verup)](https://goreportcard.com/report/github.com/catamat/verup)
[![Go Reference](https://pkg.go.dev/badge/github.com/catamat/verup.svg)](https://pkg.go.dev/github.com/catamat/verup)
[![Version](https://img.shields.io/github/tag/catamat/verup.svg?color=blue&label=version)](https://github.com/catamat/verup/releases)

Verup is a simple command line tool to increment the patch part of your version number so you just have to think about major and minor parts.
It will parse a source file to find and increment a patch var/const, it will also update a timestamp var/const if you need it.
Verup shoud be called before each build time.

## Installation:
```
go get -u github.com/catamat/verup
go install github.com/catamat/verup
```

## Options:
```
-fn [string]
	Go source file name (default "version.go")

-pn [string]
	Patch var/const name (default "versionPatch")

-tf [string]
	Timestamp output format (default "060102150405")

-tn [string]
	Timestamp var/const name (default "versionTimestamp")
```

## Usage:
Before:
```
// version.go

package main

const versionMajor = "1"
const versionMinor = "0"
const versionPatch = "0"
const versionTimestamp = ""

const version = versionMajor + "." + versionMinor + "." + versionPatch
```
Command:

```
./verup -fn version.go
```

After:
```
// version.go

package main

const versionMajor = "1"
const versionMinor = "0"
const versionPatch = "1"
const versionTimestamp = "201005155147"

const version = versionMajor + "." + versionMinor + "." + versionPatch
```