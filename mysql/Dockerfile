FROM mysql:5.7.34

# COPY ./sql/legacy_gamedata.sql /docker-entrypoint-initdb.d/legacy_gamedata.sql
# COPY ./sql/legacy_globaldata.sql /docker-entrypoint-initdb.d/legacy_globaldata.sql
# COPY ./sql/legacy_tempdb.sql /docker-entrypoint-initdb.d/legacy_tempdb.sql

COPY ./conf/my.cnf /etc/mysql/conf.d

# START MYSQL
RUN /etc/init.d/mysql start \
&& mysql --user root -ppassword -e "GRANT ALL ON mysql.* to 'root'@'%' IDENTIFIED BY 'password'; FLUSH PRIVILEGES;"

# DATABASE FILES
# COPY ./sql/legacy_gamedata.sql /usr/sql/legacy_gamedata.sql
# COPY ./sql/legacy_globaldata.sql /usr/sql/legacy_globaldata.sql
# COPY ./sql/legacy_tempdb.sql /usr/sql/legacy_tempdb.sql

# IMPORT CONTENTS
# RUN mysql --host mysqldb --port 3306 --user ${MYSQL_ROO_USER} -p${MYSQL_ROOT_PASSWORD} legacy_gamedata < /usr/sql/legacy_gamedata.sql
# RUN mysql --host mysqldb --port 3306 --user ${MYSQL_ROO_USER} -p${MYSQL_ROOT_PASSWORD} legacy_globaldata < /usr/sql/legacy_globaldata.sql
# RUN mysql --host mysqldb --port 3306 --user ${MYSQL_ROO_USER} -p${MYSQL_ROOT_PASSWORD} legacy_tempdb < /usr/sql/legacy_tempdb.sql
