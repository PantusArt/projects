up: docker-up
down: docker-down
restart: docker-down docker-up
init: docker-down-clear shop-clear docker-pull docker-build docker-up shop-init
test: shop-test

docker-up:
	docker-compose up -d

docker-down:
	docker-compose down --remove-orphans

docker-down-clear:
	docker-compose down -v --remove-orphans

docker-pull:
	docker-compose pull

docker-build:
	docker-compose build

shop-init: shop-ready

shop-clear:
	docker run --rm -v ${PWD}/shop:/app --workdir=/app alpine rm -f .ready

shop-composer-install:
	docker-compose run --rm shop-php-cli composer install


shop-ready:
	docker run --rm -v ${PWD}/shop:/app --workdir=/app alpine touch .ready

shop-test:
	docker-compose run --rm shop-php-cli php bin/phpunit
