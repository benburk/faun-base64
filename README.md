# base64

Base64 for [Faun](https://github.com/faun-lang/faun), as RFC 4648
writes it: bytes to text and back, with the standard or URL-safe alphabet,
padded or not.

```ruby
import base64 {Base64}

expect Base64.standard.encode("foobar".to_utf8()) == "Zm9vYmFy"
expect Base64.standard.decode("Zm9vYmE=") == Ok("fooba".to_utf8())
expect Base64.url_safe_unpadded.encode([251, 255]) == "-_8"
expect Base64.standard.decode("Zm9v!") == Err(Malformed)
```

`standard` and `url_safe` pad with `=`; `standard_unpadded` and
`url_safe_unpadded` don't. Decoding is strict: anything encoding would not
have written, a newline included, is `Err(Malformed)`.

## Using it

Each [release](https://github.com/faun-lang/base64/releases)'s notes give
the line to add to your package's `uses`.

## Releasing

Push a version tag. The release workflow tests the library, bundles it,
and publishes the bundle on the tag's release.

## License

[Zero-Clause BSD](LICENSE).
