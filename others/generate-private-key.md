# Generating a private Key

## Generating a private RSA key with Open SSL

install openssl on windows termial via choco

```cmd
choco install openssl
```
Generate an RSA private key, of size 2048, and output it to a file named key.pem:

```bash
openssl genrsa -out key.pem 2048

Generating RSA private key, 2048 bit long modulus
..........+++
..........................................................................+++
e is 65537 (0x10001)
```

Extract the public key from the key pair, which can be used in a certificate

```bash
openssl rsa -in key.pem -outform PEM -pubout -out public.pem

writing RSA key
```

## Generating a private EC key

Generate an EC private key, of size 256, and output it to a file named key.pem:

```bash
openssl ecparam -name prime256v1 -genkey -noout -out key.pem
```

Extract the public key from the key pair, which can be used in a certificate:

```bash
openssl ec -in key.pem -pubout -out public.pem
read EC key

writing EC key
```