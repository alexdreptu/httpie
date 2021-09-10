# Homebrew

## Files

- Local: <https://github.com/httpie/httpie/blob/master/downstream/mac/brew/httpie.rb>
- Downstream: <https://github.com/Homebrew/homebrew-core/blob/master/Formula/httpie.rb>

## Release process

First, update the current Formula:

```bash
make brew-deps
# Copy-paste content into downstream/mac/brew/httpie.rb
git add downstream/mac/brew/httpie.rb
git commit -m 'Update brew formula to XXX'
```

That [GitHub workflow](https://github.com/httpie/httpie/actions/workflows/packaging-mac-brew.yml) will test the formula when `downstream/mac/brew/httpie.rb` is changed in a pull request.

Then, open a pull request with those changes to the package file.

### :construction: Development

## :construction: Try locally
