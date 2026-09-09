# Create and Manage Cloud Storage Buckets and Encryption

## Skills Practiced

- Create Cloud Storage buckets
- Configure object ACLs
- Use customer-supplied encryption keys (CSEK)
- Configure `.boto`
- Rotate CSEK keys
- Configure lifecycle management
- Enable object versioning
- Synchronize directories
- Configure cross-project IAM access

## Key Commands

```bash
export BUCKET_NAME_1=<bucket-name>
gcloud storage cp setup.html gs://$BUCKET_NAME_1/
gsutil config -n
nano .boto
```

### CSEK = Customer-Supplied Encryption Key

A useful distinction is:

Google-managed key → Google manages the encryption key lifecycle.
CSEK → you supply the key and are responsible for keeping it available and secure.

If you lose the CSEK used to encrypt an object, you can lose access to that encrypted object.

```bash
python3 -c 'import base64; import os; print(base64.encodebytes(os.urandom(32)))'
```
### Commenting Out Encryption Settings

In `.boto`, a line beginning with `#` is treated as a comment and is not active.

Example:

```ini
# encryption_key=<OLD_CSEK>
decryption_key1=<OLD_CSEK>
encryption_key=<NEW_CSEK>
```
During key rotation:

The old encryption key can be moved to a decryption_key entry so existing objects can still be read.
The old encryption_key line can be commented out with #.
The new key becomes the active encryption_key.
After objects are re-encrypted and the old key is no longer required, remove the obsolete key from the configuration.

Commenting out a line is useful during troubleshooting because it disables the setting without immediately deleting it.

> for real systems, I would **not recommend leaving old encryption keys sitting commented out in `.boto` long-term**.
> A commented >line is still plain text in the file. Once the old key is no longer needed,
> remove it securely rather than treating `#` as a security control.
---

## Lab Objectives

This lab applies several Google Cloud Storage concepts through hands-on configuration.

### Tasks Covered

- Create Cloud Storage buckets
- Configure Access Control Lists (ACLs)
- Limit access to stored data
- Configure customer-supplied encryption keys
- Enable object versioning
- Configure Object Lifecycle Management
- Automatically archive or delete objects based on lifecycle rules
- Use directory synchronization

---

## Concepts Reinforced

This lab reinforces concepts documented in:

- Cloud Storage bucket and object architecture
- Access control
- ACLs
- Encryption
- Object versioning
- Object Lifecycle Management
- Directory synchronization

---

## Troubleshooting Lessons

### CSEK Key Generation and Formatting

The lab generates a 256-bit customer-supplied encryption key with:

```bash
python3 -c 'import base64; import os; print(base64.encodebytes(os.urandom(32)))'
```
Python returns the key as a byte-string representation that includes extra formatting characters.

### Example:

```text
b'<BASE64_AES256_KEY>\n'
```

The value entered into .boto must contain only the Base64-encoded key.

#### Incorrect format:

```text
encryption_key=b'<BASE64_AES256_KEY>\n'
```

#### Correct format:
```text
encryption_key=<BASE64_AES256_KEY>
```
### Key Lesson

When copying the generated key:

- Remove the leading b'
- Remove the trailing '
- Remove \n
- Keep the Base64 padding = at the end
- Do not add spaces or line breaks

An incorrectly formatted CSEK can prevent Cloud Storage from encrypting or decrypting objects successfully.

## Operational Takeaways

- Verify environment variables before using bucket commands.
- Keep encryption and decryption keys clearly documented during key rotation.
- Review `.boto` carefully before retrying failed CSEK operations.
- Treat customer-supplied encryption keys as sensitive credentials.
- Use temporary placeholder values in public documentation instead of real active keys.
