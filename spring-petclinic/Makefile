.PHONY: build_and_run
build_and_run: build run

.PHONY: build
build:
	docker build . -t spring-petclinic

.PHONY: run
run:
	docker run -d --rm --init -p 3001:3000 -p 8081:8080 --name spring-petclinic spring-petclinic

.PHONY: stop
stop:
	docker stop spring-petclinic
