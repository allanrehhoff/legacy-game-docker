FROM mysql:5.7.34

# DATABASE FILES
# COPY ./sql/legacy_gamedata.sql /usr/sql/legacy_gamedata.sql
# COPY ./sql/legacy_globaldata.sql /usr/sql/legacy_globaldata.sql
# COPY ./sql/legacy_tempdb.sql /usr/sql/legacy_tempdb.sql

COPY ./sql/legacy_gamedata.sql /docker-entrypoint-initdb.d/legacy_gamedata.sql
COPY ./sql/legacy_globaldata.sql /docker-entrypoint-initdb.d/legacy_globaldata.sql
COPY ./sql/legacy_tempdb.sql /docker-entrypoint-initdb.d/legacy_tempdb.sql

# START MYSQL
RUN /etc/init.d/mysql start

# IMPORT CONTENTS
# RUN mysql --host mysqldb --port 3306 --user ${MYSQL_ROO_USER} -p${MYSQL_ROOT_PASSWORD} legacy_gamedata < /usr/sql/legacy_gamedata.sql
# RUN mysql --host mysqldb --port 3306 --user ${MYSQL_ROO_USER} -p${MYSQL_ROOT_PASSWORD} legacy_globaldata < /usr/sql/legacy_globaldata.sql
# RUN mysql --host mysqldb --port 3306 --user ${MYSQL_ROO_USER} -p${MYSQL_ROOT_PASSWORD} legacy_tempdb < /usr/sql/legacy_tempdb.sql