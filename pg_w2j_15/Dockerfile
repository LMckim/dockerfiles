FROM postgres:15-alpine

RUN apk add git make gcc musl-dev clang15 llvm15
RUN git clone https://github.com/eulerto/wal2json.git


WORKDIR /wal2json
RUN alias clang-15=clang
RUN make 
RUN make install 

WORKDIR /
RUN mkdir /var/pgdata
RUN chown -R postgres:postgres /var/pgdata/
ENV PGDATA="/var/pgdata"
RUN su - postgres -c 'initdb -D "/var/pgdata"'

COPY conf /var/pgdata/postgresql.conf
