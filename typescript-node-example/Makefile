.PHONY: build_and_run
build_and_run: build run

.PHONY: build
build:
	docker build . -t typescript-node-example

.PHONY: run
run:
	docker run -d --rm --init -p 3002:3000 -p 8082:8080 --name typescript-node-example typescript-node-example

.PHONY: stop
stop:
	docker stop typescript-node-example
