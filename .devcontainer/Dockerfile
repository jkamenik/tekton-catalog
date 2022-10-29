FROM golang:1.19-alpine

# Otherwise we get strange issues
ENV CGO_ENABLED=0

# Install useful go commands
RUN go install -v golang.org/x/tools/gopls@latest \
    && go install github.com/go-delve/delve/cmd/dlv@latest \
    && go install github.com/fatih/gomodifytags@latest \
    && go install github.com/cweill/gotests/gotests@latest \
    && go install github.com/josharian/impl@latest \
    && go install honnef.co/go/tools/cmd/staticcheck@latest \
    && go install -v github.com/ramya-rao-a/go-outline@latest

# Install other useful tools
RUN apk add --no-cache \
    bash \
    git \
    openssh