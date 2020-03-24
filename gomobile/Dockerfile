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

RUN wget https://dl.google.com/android/repository/commandlinetools-linux-6200805_latest.zip
RUN unzip commandlinetools-linux-6200805_latest.zip
RUN rm -f commandlinetools-linux-6200805_latest.zip

ENV ANDROID_HOME=/root/android-sdk-linux

RUN yes | /root/tools/bin/sdkmanager --sdk_root=${ANDROID_HOME} --licenses
RUN /root/tools/bin/sdkmanager --sdk_root=${ANDROID_HOME} "platform-tools" "platforms;android-26"

ENV ANDROID_NDK_HOME=/root/android-ndk-r21
RUN wget https://dl.google.com/android/repository/android-ndk-r21-linux-x86_64.zip
RUN unzip android-ndk-r21-linux-x86_64.zip
RUN rm -f android-ndk-r21-linux-x86_64.zip


