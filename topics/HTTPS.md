# HTTPS
HTTP over TLS

## Best Practices
- Use HTTPS _everywhere_
- SSL certs are made public by the CAs. If you get a cert for a domain, that domain is now public.
- Use Strict Transport Security (STS) with a max age of at least a year
- Use HSTS preferably on the top level domain and potentially implement preloading once your setup is sufficiently tried and tested
- Add DNS CAA (Certificate Authority Authorization). Add a fallback CA.
- Setup a Certificate Transparency monitoring process
- Don't use Public Key Pinning for web apps, it's too fragile and can be exploitet (PKP ransom). Use it only if you have an out-of-band update channel.
