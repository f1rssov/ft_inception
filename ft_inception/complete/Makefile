name = inception
all:
	@mkdir ~/data/
	@mkdir ~/data/wordpress
	@mkdir ~/data/mariadb
	@docker-compose -f ./srcs/docker-compose.yml --env-file srcs/.env up -d

build:
	@docker-compose -f ./srcs/docker-compose.yml --env-file srcs/.env up -d --build

down:
	@docker-compose -f ./srcs/docker-compose.yml --env-file srcs/.env down

eval:
	@bash ./srcs/requirements/tools/eval.sh

re: down clean
	@mkdir ~/data/wordpress
	@mkdir ~/data/mariadb
	@docker-compose -f ./srcs/docker-compose.yml --env-file srcs/.env up -d --build

clean: down
	@docker system prune -a --force
	@sudo rm -rf ~/data/wordpress
	@sudo rm -rf ~/data/mariadb

fclean:
	@docker stop $$(docker ps -qa)
	@docker system prune --all --force --volumes
	@docker network prune --force
	@docker volume prune --force
	@sudo rm -rf ~/data/wordpress
	@sudo rm -rf ~/data/mariadb

.PHONY	: all build down re clean fclean
