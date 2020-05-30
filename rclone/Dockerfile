FROM alpine

ENV arch=amd64
ENV ver=v1.52.0

RUN wget https://github.com/rclone/rclone/releases/download/${ver}/rclone-${ver}-linux-${arch}.zip
RUN unzip rclone-${ver}-linux-${arch}.zip
RUN mv rclone-${ver}-linux-${arch}/rclone /usr/bin/rclone
RUN rm -r rclone*

ENTRYPOINT ["/usr/bin/rclone"]

CMD ["--version"]
