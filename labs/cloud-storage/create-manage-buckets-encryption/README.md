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

### Multiple CSEK Decryption Keys

The `.boto` configuration supports multiple `decryption_key` entries:

```ini
decryption_key1=<OLD_CSEK_1>
decryption_key2=<OLD_CSEK_2>
decryption_key3=<OLD_CSEK_3>
```
This allows gsutil to access objects that were encrypted with different customer-supplied encryption keys, which is particularly useful during CSEK key rotation.

The active encryption_key is used for new writes, while numbered decryption_key entries provide access to objects encrypted with previous keys.

> Multiple decryption keys support safe key rotation by allowing applications to continue reading objects
> encrypted with previous CSEKs while new data is encrypted with the current key.

Imagine a company stores backups in Cloud Storage:

- January files were encrypted with Key A
- April files were encrypted with Key B
- July files were encrypted with Key C
- New files are now encrypted with Key D

You could configure:
```ini
encryption_key=<KEY_D>

decryption_key1=<KEY_A>
decryption_key2=<KEY_B>
decryption_key3=<KEY_C>
```
Now new objects use Key D, while older objects can still be read with A, B, or C.

That matters in situations like security policy changes, suspected key exposure, periodic key rotation, mergers between systems, or staged migrations. Instead of re-encrypting every object immediately, you can keep the old decryption keys available while gradually moving data to the new key.

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

---

## Task 5. Enable Lifecycle Management

Object Lifecycle Management automatically performs actions on Cloud Storage objects when defined conditions are met.

Common lifecycle actions include:

- Change an object's storage class
- Delete objects after a specified age
- Retain only a certain number of object versions

Example use cases:

- Move older objects from Standard to Nearline or Coldline storage
- Delete temporary objects after a set number of days
- Automatically clean up older object versions

### Why It Matters

Lifecycle policies reduce manual administration and can lower storage costs by automatically managing data based on age, storage class, or other object conditions.

See also: [Cloud Storage Lifecycle Policy Flow](../../../architecture-diagrams/storage/gcs-lifecycle-policy-flow/)

---

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
