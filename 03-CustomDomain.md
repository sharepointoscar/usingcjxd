# Adding a Custom Domain

As you might have noticed, Jenkins X automatically used a domain with **np.io** for all of the endpoints.

That is helpful, but let's get real here, we know we use custom domains for external corporate endpoints and apps.

So lets configure this now.

> **NOTE:** If you are on OS X, you cannot install it via Homebrew, as that is a different version.

```bash
curl -L https://storage.googleapis.com/artifacts.jenkinsxio.appspot.com/binaries/cjxd/latest/jx-darwin-amd64.tar.gz | tar xzv

# move the executable to proper location
sudo mv jx /usr/local/bin

# validate binary is in proper location
which jx

# lastly check the version
jx --version
```