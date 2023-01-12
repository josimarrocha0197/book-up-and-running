# ETAPA 1: Construcao
FROM golang:1.11-alpine AS build

# Instala Node e NPM
RUN apk update && apk upgrade && apk add --no-cache git nodejs bash npm

# Obtem as dependencias para a parte Go da construcao
RUN go get -u github.com/jteeuwen/go-bindata/...
RUN go get github.com/tools/godep

WORKDIR /go/src/github.com/kubernetes-up-and-running/kuard

# Copia todos os codigos-fontes
COPY . .

# Este e um conjunto de variaveis esperado pelo script de construcao
ENV VERBOSE=0
ENV PKG=github.com/kubernetes-up-and-running/kuard
ENV ARCH=amd64
ENV VERSION=test

# Faz a construcao. O script faz parte dos codigos-fontes de entrada
RUN build/build.sh

# ETAPA 2: Implantacao
FROM alpine

USER nobody:nobody
COPY --from=build /go/bin/kuard /kuard

CMD [ "/kuard" ]