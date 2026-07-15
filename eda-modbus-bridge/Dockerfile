ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG=C.UTF-8

WORKDIR /app

RUN curl -fsSL https://deb.nodesource.com/setup_22.x | bash -

RUN apt-get -y update && \
    apt-get -y install --no-install-recommends git-core nodejs gcc g++ make && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/lsandini/eda-modbus-bridge.git eda-modbus-bridge
    
RUN cd eda-modbus-bridge && \
    npm install && \
    npm run build

COPY config.sh /app/config.sh
RUN chmod +x /app/config.sh

COPY entrypoint.sh /app/entrypoint.sh
RUN chmod +x /app/entrypoint.sh

CMD ["/app/entrypoint.sh"]
