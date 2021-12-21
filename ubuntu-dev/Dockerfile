FROM ubuntu:16.04
RUN apt-get update &&  apt-get install -y build-essential cmake gdb openssh-server rsync
RUN mkdir -p /var/run/sshd && sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config && echo 'root:123456' |chpasswd
RUN sed -ri 's/RSYNC_ENABLE=false/RSYNC_ENABLE=true/g' /etc/default/rsync && mkdir /root/sync
COPY rsync.conf /etc
COPY entrypoint.sh /sbin
RUN chmod +x /sbin/entrypoint.sh
ENTRYPOINT [ "/sbin/entrypoint.sh" ]
