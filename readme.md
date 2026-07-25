```bash
# Create in pem
openssl req -x509 -newkey rsa:4096 -nodes -out server.crt -keyout server.key -days 3650 -subj "/CN=localhost"
```

```bash
# Convert to pfx
openssl pkcs12 -export -inkey server.key -in server.crt -passout pass:root -out server.pfx
```