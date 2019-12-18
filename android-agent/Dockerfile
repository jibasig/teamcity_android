FROM jetbrains/teamcity-agent:latest

LABEL maintainer="barth.heiko@gmail.com"

ENV ANDROID_HOME /opt/android-sdk-linux
ENV ANDROID_SDK_TOOLS_VERSION 4333796
ENV SHELL /bin/bash
ENV PATH "$ANDROID_HOME/platform-tools:$PATH"
ENV PATH "$ANDROID_HOME/tools/bin:$PATH"
ENV PATH "$ANDROID_HOME/tools:$PATH"

RUN apt-get update \
        && apt-get install -y --no-install-recommends \
                wget file language-pack-en unzip

# Fix locale.
ENV LANG en_US.UTF-8
ENV LC_CTYPE en_US.UTF-8
RUN locale-gen en_US && update-locale LANG=en_US.UTF-8 LC_CTYPE=en_US.UTF-8

# Install Android command line tools
RUN mkdir -p $ANDROID_HOME \
    && chmod 777 $ANDROID_HOME \
    && wget -nc https://dl.google.com/android/repository/sdk-tools-linux-${ANDROID_SDK_TOOLS_VERSION}.zip \
    && unzip sdk-tools-linux-${ANDROID_SDK_TOOLS_VERSION}.zip -d $ANDROID_HOME \
    && rm sdk-tools-linux-${ANDROID_SDK_TOOLS_VERSION}.zip

# Install Android licenses to not accept them manually during builds
RUN yes | $ANDROID_HOME/tools/bin/sdkmanager --licenses


