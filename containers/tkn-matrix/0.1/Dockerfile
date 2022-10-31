FROM golang:1.19-alpine as builder

# Otherwise we get strange issues
ENV CGO_ENABLED=0

WORKDIR /code
COPY . /code
# RUN go test ./... && go install .

FROM alpine
LABEL Repo "jkamenik/"
LABEL Tag "jkamenik/tkn-matrix:0.1-latest"

# COPY --from=builder /go/bin/matrix /usr/local/bin

RUN apk add --no-cache tini

ENTRYPOINT [ "/tini", "--" ]
CMD [ "/usr/local/bin/matrix" ]