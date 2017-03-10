FROM openjdk:8-jre-alpine
MAINTAINER Sudhir Nimavat

ENV CI_GROOVY_VERSION=2.4.5 #work around for issue https://github.com/grails/grails-core/issues/10011 for grails 2.5.5
ENV GRAILS_VERSION 2.5.5
WORKDIR /usr/lib/jvm

RUN apk update && apk add ca-certificates wget && update-ca-certificates && \
    wget https://github.com/grails/grails-core/releases/download/v${GRAILS_VERSION}/grails-${GRAILS_VERSION}.zip && \
    unzip grails-${GRAILS_VERSION}.zip && \
    rm -rf grails-${GRAILS_VERSION}.zip && \
    ln -s grails-${GRAILS_VERSION} grails

ENV GRAILS_HOME /usr/lib/jvm/grails
ENV PATH $GRAILS_HOME/bin:$PATH

RUN mkdir /app
WORKDIR /app

ENTRYPOINT ["grails"]
CMD ["-version"]