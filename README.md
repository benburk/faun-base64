# base64

Base64 for [Faun](https://github.com/faun-lang/faun), as RFC 4648
writes it: bytes to text and back, in the standard or URL-safe alphabet.

```ruby
import base64 {encode, decode, encode_url, decode_url}

expect encode("foobar".to_utf8()) == "Zm9vYmFy"
expect decode("Zm9vYmE=") == Ok("fooba".to_utf8())
expect encode_url([251, 255]) == "-_8"
expect decode("Zm9v!") == Err(Malformed)
```

`encode` writes the standard alphabet, padded; `encode_url` writes the
URL-safe one, unpadded, as JSON Web Tokens do. Both decoders take a text with
its padding or without it, and refuse anything else encoding would not have
written, a newline included.

## Using it

Each [release](https://github.com/faun-lang/base64/releases)'s notes give
the line to add to your package's `uses`.

## Releasing

Push a version tag. The release workflow tests the library, bundles it,
and publishes the bundle on the tag's release.

## License

[Zero-Clause BSD](LICENSE).
