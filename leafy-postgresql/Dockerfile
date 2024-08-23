# PostgreSQL 13 버전을 베이스 이미지로 사용
FROM postgres:13

# init.sql 파일을 /docker-entrypoint-initdb.d/ 로 복사
# /docker-entrypoint-initdb.d/ 에 있는 sql문은 컨테이너가 처음 실행시 자동 실행됨.
COPY ./init/init.sql /docker-entrypoint-initdb.d/

# postgresql.conf 파일을 /etc/postgresql/custom.conf 로 복사
# 기본 설정 파일을 덮어쓰기하여 새로운 설정 적용
COPY ./config/postgresql.conf /etc/postgresql/custom.conf

# 계정정보 설정을 위한 환경변수 지정
ENV POSTGRES_USER=myuser
ENV POSTGRES_PASSWORD=mypassword
ENV POSTGRES_DB=mydb

# postgres 가 사용하는 포트 지정
EXPOSE 5432

# CMD 지정
# postgres 를 실행하는 명령인 postgres 와 -c 옵션을 통해서 config 파일 지정
# 설정 파일을 직접 지정하면, 이미지 안에있는 기본 디폴트 설정 파일을 사용하지 않고, 지정한 설정파일을 사용한다.
CMD ["postgres", "-c", "config_file=/etc/postgresql/custom.conf"]
