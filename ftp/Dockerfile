
FROM ubuntu:24.04

RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends vsftpd \
    && useradd --create-home --home-dir /home/alumno1 --shell /bin/bash alumno1 \
    && mkdir -p /var/run/vsftpd/empty /var/ftp /home/alumno1/archivos \
    && chown root:root /var/run/vsftpd/empty /home/alumno1 \
    && chmod 555 /var/run/vsftpd/empty \
    && chmod 755 /home/alumno1 \
    && chown alumno1:alumno1 /home/alumno1/archivos \
    && chmod 755 /var/ftp \
    && rm -rf /var/lib/apt/lists/*

COPY vsftpd.conf /etc/vsftpd.conf

EXPOSE 21 21100-21110

CMD ["/usr/sbin/vsftpd", "/etc/vsftpd.conf"]
