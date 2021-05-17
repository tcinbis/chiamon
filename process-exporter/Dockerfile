FROM golang:1.15 AS build
#RUN curl -L -s https://github.com/golang/dep/releases/download/v0.5.0/dep-linux-amd64 -o $GOPATH/bin/dep
#RUN chmod +x $GOPATH/bin/dep
RUN git clone https://github.com/ncabatoff/process-exporter.git /go/src/github.com/ncabatoff/process-exporter
WORKDIR /go/src/github.com/ncabatoff/process-exporter
# ADD . .
#RUN dep ensure

# Build the process-exporter command inside the container.
RUN make

FROM scratch

COPY --from=build /go/src/github.com/ncabatoff/process-exporter/process-exporter /bin/process-exporter

# Run the process-exporter command by default when the container starts.
ENTRYPOINT ["/bin/process-exporter"]
