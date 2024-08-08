FROM alpine:latest

# Install the required packages
RUN apk add --update tor iptables sudo

# Expose the ports made available through Tor
EXPOSE 9001 9040 9050 5353/udp

# Populate the tor-router configurations
ADD https://raw.githubusercontent.com/ric866/tor-router/master/src/entrypoint.sh /opt/tor-router/entrypoint.sh
ADD https://raw.githubusercontent.com/ric866/tor-router/master/src/iptables.rules /opt/tor-router/iptables.rules
ADD https://raw.githubusercontent.com/ric866/tor-router/master/src/torrc /opt/tor-router/torrc

RUN chmod -R 765 /opt/tor-router/

# Set the container's WORKDIR and ENTRYPOINT
WORKDIR /opt/tor-router
ENTRYPOINT ["/opt/tor-router/entrypoint.sh"]
