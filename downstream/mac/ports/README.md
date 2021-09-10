# MacPorts

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/mac/ports/Portfile>
- Downstream: <https://github.com/macports/macports-ports/blob/master/net/httpie/Portfile>

## Release process

Open a pull request to update the package file ([example](https://github.com/macports/macports-ports/pull/12167)).

- Here is how to calculate the size and checksums (replace `2.5.0` with the correct version):

  ```bash
  # Download the archive
  $ wget https://api.github.com/repos/httpie/httpie/tarball/2.5.0

  # Size
  $ stat --printf="%s\n" 2.5.0
  1105185

  # Checksums
  $ openssl dgst -rmd160 2.5.0
  RIPEMD160(2.5.0)= 88d227d52199c232c0ddf704a219d1781b1e77ee
  $ openssl dgst -sha256 2.5.0
  SHA256(2.5.0)= 00c4b7bbe7f65abe1473f37b39d9d9f8f53f44069a430ad143a404c01c2179fc
  ```

- The commit message must be `httpie: update to XXX`.

### :construction: Development

## :construction: Try locally
