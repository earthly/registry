ARG TARGET_SHA=a1e30cca

build:
    FROM golang:1.16

    GIT CLONE --branch=main https://github.com/docker/distribution distribution
    RUN cd distribution && git checkout $TARGET_SHA && make binaries

    SAVE ARTIFACT distribution/bin/registry

docker:
    FROM registry:2.7

    COPY +build/registry /bin/registry
    SAVE IMAGE --push dchw/registry:$TARGET_SHA