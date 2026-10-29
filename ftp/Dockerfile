
FROM ubuntu:24.04

RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends vsftpd \
    && useradd --create-home --home-dir /home/alumno1 --shell /bin/bash alumno1 \
    && useradd --create-home --home-dir /home/alumno2 --shell /bin/bash alumno2 \
    && useradd --create-home --home-dir /home/alumno3 --shell /bin/bash alumno3 \
    && echo 'alumno1:1234' | chpasswd \
    && echo 'alumno2:1234' | chpasswd \
    && echo 'alumno3:1234' | chpasswd \
    && mkdir -p /var/run/vsftpd/empty /var/ftp \
       /home/alumno1/archivos /home/alumno2/archivos /home/alumno3/archivos \
    && chown root:root /var/run/vsftpd/empty /home/alumno1 /home/alumno2 /home/alumno3 \
    && chmod 555 /var/run/vsftpd/empty \
    && chmod 755 /home/alumno1 /home/alumno2 /home/alumno3 /var/ftp \
    && chown alumno1:alumno1 /home/alumno1/archivos \
    && chown alumno2:alumno2 /home/alumno2/archivos \
    && chown alumno3:alumno3 /home/alumno3/archivos \
    && rm -rf /var/lib/apt/lists/*

COPY vsftpd.conf /etc/vsftpd.conf
COPY usuarios/ /etc/vsftpd_user_conf/

EXPOSE 21 21100-21110

CMD ["/usr/sbin/vsftpd", "/etc/vsftpd.conf"]
