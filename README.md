# Infisical for LazyCat

LazyCat LPK v2 packaging for [Infisical](https://github.com/Infisical/infisical), an open-source platform for secrets, certificates, and privileged access management.

## Runtime

- Runs `infisical/infisical:v0.165.3` through the `docker.1ms.run` mirror.
- Uses PostgreSQL 14 and Redis 7 with persistent application storage.
- The site URL is derived from the LazyCat application domain.
- Encryption, authentication, cookie-signing, and database secrets use separate stable installation secrets; the public sample values from upstream are not used.
- The complete UI remains behind LazyCat authentication.
- LazyCat OIDC, automatic login injection, and file-picker interception are intentionally omitted as requested.

The supplied 350×350 logo was resized to the required 512×512 PNG.

The LazyCat store already contains `cloud.lazycat.app.infisical`. This repository intentionally uses the distinct package ID `community.lazycat.app.infisical` as explicitly requested.

## License note

The upstream root license grants MIT terms to content outside `ee/`; enterprise-edition directories carry their own license. This package records the open-source core license as MIT.

## Build

```sh
lzc-cli project release -o dist/application.lpk
```

## GitHub Actions

The scheduled workflow follows stable SemVer tags for `infisical/infisical`, creates a versioned GitHub Release asset, and publishes only to the MiaoMiao private store.

Required repository or organization Secrets:

- `APPSTORE_URL`
- `APPSTORE_TOKEN`

Optional Secrets:

- `APP_ID`
- `PRIVATE_STORE_GROUP_CODES`
