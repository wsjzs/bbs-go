FROM golang:alpine3.16 AS build

WORKDIR /server
# 构建
ENV GOPROXY=https://goproxy.cn
COPY ./server/go.mod ./
COPY ./server/go.sum ./
RUN go mod download
COPY ./server .
RUN go build -v .

# 部署
FROM golang:alpine3.16 
WORKDIR /server

COPY --from=build /server ./

CMD ./bbs-go

EXPOSE 8082