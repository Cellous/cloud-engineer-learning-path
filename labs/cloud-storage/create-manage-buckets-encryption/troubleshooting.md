# Troubleshooting Lessons

## Invalid Content-Language

The generated `.boto` configuration caused:

`400 Invalid content language`

The `content_language` setting was disabled before retrying the upload.

## CSEK Key Handling

CSEK keys must remain exact Base64-encoded AES-256 values.
The encryption and decryption keys in `.boto` must correspond to
the key used when the object was written.

## Key Lesson

When an operation fails:

Verify the bucket environment variable.
Verify the object exists.
Verify the active encryption/decryption key.
Inspect `.boto`.
Retry the exact lab command.
