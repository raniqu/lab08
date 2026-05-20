# Отчет к лабораторной работе 8

## Что сделано
Нужно было завернуть приложение из lab07 в Docker.

## Dockerfile

```
arina@debian:~/raniqu/workspace/lab08$ cat Dockerfile
FROM ubuntu:18.04

RUN apt update
RUN apt install -yy gcc g++ cmake

# Обновляем CMake до версии 3.14+
RUN apt install -yy wget
RUN wget -qO- "https://cmake.org/files/v3.20/cmake-3.20.0-linux-x86_64.tar.gz" | tar --strip-components=1 -xz -C /usr/local

COPY . print/
WORKDIR print

RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
RUN cmake --build _build
RUN cmake --build _build --target install

ENV LOG_PATH /home/logs/log.txt

VOLUME /home/logs

WORKDIR _install/bin

ENTRYPOINT ["./demo"]
```
## Сборка образа

```
arina@debian:~/raniqu/workspace/lab08$ docker build -t logger .
```

```
arina@debian:~/raniqu/workspace/lab08$ docker images
                                                                                  i Info →   U  In Use
IMAGE           ID             DISK USAGE   CONTENT SIZE   EXTRA
logger:latest   2b82ff2ddae2        691MB          189MB
```


Docker работает. Приложение внутри контейнера собирается, запускается, логи сохраняются
