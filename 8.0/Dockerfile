FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base

# ENV ASPNETCORE_URLS=https://+;http://+
ENV ASPNETCORE_HTTP_PORTS=8080
ENV ASPNETCORE_HTTPS_PORTS=8443
ENV ASPNETCORE_Kestrel__Certificates__Default__Password=root
ENV ASPNETCORE_Kestrel__Certificates__Default__Path=/https/server.pfx

RUN mkdir -p /https
WORKDIR /https
# RUN openssl req -x509 -newkey rsa:4096 -nodes -out server.crt -keyout server.key -days 3650 -subj "/CN=localhost"
# RUN openssl pkcs12 -export -inkey server.key -in server.crt -passout pass:root -out server.pfx
COPY server.pfx .
RUN chmod 755 server.pfx 

USER $APP_UID
WORKDIR /app
RUN mkdir obj
RUN chown $APP_UID obj
RUN mkdir wwwroot2
RUN chown $APP_UID wwwroot2

# Print dotnet version
RUN dotnet --info

# HTTP (default)
EXPOSE $ASPNETCORE_HTTP_PORTS

# HTTPS (default)
EXPOSE $ASPNETCORE_HTTPS_PORTS