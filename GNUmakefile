BUILD_ENV=CGO_ENABLED=0
TAG=$(shell PAGER= git tag --points-at HEAD)
BRANCH=$(subst /,-,$(shell git branch --show-current))
VERSION=$(if $(VER),$(VER),$(if $(TAG),$(TAG),$(BRANCH)))
BIN_NAME := terraform-provider-test_$(VERSION)

default: build

build:
	@echo "Building version $(VERSION)"
	$(BUILD_ENV) go build -o $(BIN_NAME) $(ARGS)

build-linux:
	@echo "Building version $(VERSION) for linux"
	env $(BUILD_ENV) GOOS=linux GOARCH=amd64 go build -o $(BIN_NAME) $(ARGS)

.PHONY: build build-linux
