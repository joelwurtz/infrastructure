#
# Image      jolicode/serf
# Maintainer Joel Wurtz <jwurtz@jolicode.com>
#

FROM base/arch
MAINTAINER Joel Wurtz <jwurtz@jolicode.com>

# Serf install
RUN pacman -Syu --noconfirm
RUN pacman -Sy --noconfirm unzip supervisor
RUN curl https://dl.bintray.com/mitchellh/serf/0.3.0_linux_amd64.zip -L -o /home/serf.zip && cd /home && unzip serf.zip && mv /home/serf /usr/bin/serf && rm /home/serf.zip

ADD bin/serf-agent /usr/bin/serf-agent
ADD supervisor/supervisord.conf     /etc/supervisord.conf
ADD supervisor/supervisor-serf.conf /etc/supervisor.d/serf.conf

RUN chmod +x /usr/bin/serf-agent

CMD supervisord -n -c /etc/supervisord.conf