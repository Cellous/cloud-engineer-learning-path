# Troubleshooting Lessons

## Invalid Content-Language

The generated `.boto` configuration caused:

`400 Invalid content language`

The `content_language` setting was disabled before retrying the upload.

## CSEK Key Handling

CSEK keys must remain exact Base64-encoded AES-256 values.
The encryption and decryption keys in `.boto` must correspond to
the key used when the object was written.

---

## Configuration Recovery

### Troubleshooting Procedure
### Recreate or Locate the `.boto` Configuration File

If `.boto` is empty or missing, generate a new configuration file with:

```bash
gsutil config -n
```

Then open it with:
```bash
nano ~/.boto
```
If the expected configuration still does not appear, inspect the active `gsutil` configuration and installation details with:
```bash
gsutil version -l
```
This can help identify which configuration path `gsutil` is using.

>`gsutil version -l` does not directly “locate `.boto`” in every case,
> but it can show configuration-path information and help diagnose which config is active.

---

## Key Lesson

When an operation fails:

Verify the bucket environment variable.
Verify the object exists.
Verify the active encryption/decryption key.
Inspect `.boto`.
Retry the exact lab command.
