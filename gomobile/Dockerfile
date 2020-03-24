FROM centos:7

ENV GOROOT=/root/go
ENV GOPATH=/home/go
ENV PATH="/home/go/bin:/root/go/bin:${PATH}"

RUN yum install -y git unzip wget && yum -y clean all && \
    rm -rf /var/cache/yum

WORKDIR /root

RUN wget https://dl.google.com/go/go1.14.1.linux-amd64.tar.gz && tar -xvf go1.14.1.linux-amd64.tar.gz && rm -f go1.14.1.linux-amd64.tar.gz

RUN go get golang.org/x/mobile/cmd/gomobile && go get -d golang.org/x/mobile/example/basic

RUN yum -y install java && yum -y clean all && \
    rm -rf /var/cache/yum
ENV JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.242.b08-0.el7_7.x86_64/jre
ENV ANDROID_HOME=/root/android-sdk-linux
ENV ANDROID_NDK_HOME=/root/android-ndk-r21
