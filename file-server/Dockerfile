FROM alpine

LABEL Andrew Mcshane <andrew@ns1.ovh>

RUN apk --no-cache add \
    samba \
    samba-common-tools
RUN mkdir -p /data

VOLUME ["/data"]

COPY smb.conf /etc/samba/smb.conf

EXPOSE 445

ENTRYPOINT ["smbd", "-FS"]
