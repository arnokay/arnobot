# TODO

[ ] - add whitelist
[ ] - handle todo's
[ ] - add kick

# steps for local deploy

## creating environment variables

rename `.env.example` to `.env` in root directory
rename `.env.auth.example` to `.env.auth` in root directory
rename `.env.twitch.example` to `.env.twitch` in root directory
rename `.env.core.example` to `.env.core` in root directory

fill in env variables

## start docker compose

```bash
docker compose -c docker-compose.nightly.yaml up -d
```

## apply migrations

we need to checkout shared repository, where all migrations are stored

```bash
git submodule update --init shared
cd shared
```

for migrations i use atlasgo.io so either follow thier install procedure or run this:

```bash
curl -sSf https://atlasgo.sh | sh
```

rename `.env.example` to `.env` in shared root directory

fill in env variables

after all that use atlas to apply migrations:
```bash
atlas migrate apply --local
```

---

missing steps:
[] setting up default bots (by first login or something like this)
