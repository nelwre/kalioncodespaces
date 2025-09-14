FROM kalilinux
ENV USERNAME=user
ENV PASSWORD=1234
ENV container docker
ENV DEBIAN_FRONTEND=noninteractive

# systemd setup
RUN apt-get update \
    && apt-get install --no-install-recommends -y sudo locales rsyslog systemd dbus systemd-cron \
    && rm -f /usr/local/bin/systemctl \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

    # user setup
RUN useradd -m -s /bin/bash $USERNAME && \
    echo "$USERNAME:$PASSWORD" | chpasswd && \
    usermod -aG sudo $USERNAME

# systemd as 1st process
STOPSIGNAL SIGRTMIN+3
CMD ["/sbin/init"]

