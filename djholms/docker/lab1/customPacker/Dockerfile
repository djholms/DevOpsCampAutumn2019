FROM alpine:latest
MAINTAINER "The Packer Team <packer@hashicorp.com>"

ARG PACKER_VERSION=1.4.5
ENV PACKER_VERSION=${PACKER_VERSION} 
ENV PACKER_SHA256SUM=b4dc37877a0fd00fc72ebda98977c2133be9ba6b26bcdd13b1b14a369e508948

RUN apk add --update git bash wget openssl

ADD https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_linux_amd64.zip ./
ADD https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_SHA256SUMS ./

RUN sed -i '/.*linux_amd64.zip/!d' packer_${PACKER_VERSION}_SHA256SUMS
RUN sha256sum -cs packer_${PACKER_VERSION}_SHA256SUMS
RUN unzip packer_${PACKER_VERSION}_linux_amd64.zip -d /bin
RUN rm -f packer_${PACKER_VERSION}_linux_amd64.zip

#RUN useradd packer
#USER packer
#ENV USER packer

ENTRYPOINT ["/bin/packer"]
CMD ["--version"]
