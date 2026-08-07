# Length Extension (`length-extension`)

**Category:** cryptography · **Difficulty:** hard · **Points:** 400

A naive MAC = H(secret || msg) is forgeable; extend it to sign an admin request.

## Run it

```bash
docker build -t picoclone/length-extension .
# `picoclone start length-extension` (or the web UI) prints the docker run line with your
# PICOCLONE_SERVER + PICOCLONE_INSTANCE_TOKEN
```

## Recover the flag

The delivery blob is Fernet ciphertext. Discover the key seed, derive the Fernet key, then decrypt.

The plaintext flag is never written to disk or served — only the encoded delivery blob
is. When you have it:

```bash
picoclone submit length-extension 'picoclone{...}'
```

## Hints

- Merkle–Damgård hashes leak enough state to continue hashing.
- Append your data plus padding to forge a valid MAC.
