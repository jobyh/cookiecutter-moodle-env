.PHONY: install-db upgrade-db dummy-content phpunit-init purge-caches

DB_NAME={{ cookiecutter.db_name }}
DB_USER={{ cookiecutter.db_user }}
DB_PASS={{ cookiecutter.db_pass }}

DB_CHARSET=utf8
#DB_CHARSET=utf8mb4
DB_COLLATE=utf8_unicode_ci
#DB_COLLATE=utf8mb4_unicode_ci

ADMIN_PASS={{ cookiecutter.admin_pass }}
ADMIN_EMAIL={{ cookiecutter.admin_email }}

SITE_FULLNAME={{ cookiecutter.site_fullname }}
SITE_SHORTNAME={{ cookiecutter.site_shortname }}

DIRROOT={{ cookiecutter.dirroot }}
install-db:
	docker-compose exec db-mysql mysql -u root -pRoot123. -e 'DROP DATABASE IF EXISTS ${DB_NAME}; CREATE DATABASE ${DB_NAME} DEFAULT CHARACTER SET ${DB_CHARSET} COLLATE ${DB_COLLATE}; GRANT ALL ON ${DB_NAME}.* TO ${DB_USER} IDENTIFIED BY "${ADMIN_PASS}"'
	docker-compose exec webserver php ${DIRROOT}/admin/cli/install_database.php \
		--agree-license \
		--adminpass=${ADMIN_PASS} \
		--adminemail=${ADMIN_EMAIL} \
		--fullname='${SITE_FULLNAME}' \
		--shortname='${SITE_SHORTNAME}'

upgrade-db:
	docker-compose exec webserver php ${DIRROOT}/admin/cli/upgrade.php --non-interactive

dummy-content:
	docker-compose exec webserver php ${DIRROOT}/admin/tool/generator/cli/maketestsite.php --size=M

phpunit-init:
	docker-compose exec webserver chown www-data:www-data /var/www/html
	docker-compose exec -u www-data webserver php ${DIRROOT}/admin/tool/phpunit/cli/init.php

purge-caches:
	docker-compose exec -u www-data webserver php ${DIRROOT}/admin/cli/purge_caches.php
