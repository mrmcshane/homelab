FROM alpine

RUN apk --no-cache add samba samba-common-tools
RUN mkdir -p /data

VOLUME ["/data"]

COPY smb.conf /etc/samba/smb.conf

EXPOSE 445

ENTRYPOINT ["smbd", "-FS"]
