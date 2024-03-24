# Pocketbase Docker Template

## Dokku Instructions

1. Clone this repository
2. Run `cd dokku-pocketbase`
3. Create Dokku App in your server `dokku apps:create pocketbase`
4. Create a Persistent Storage `dokku storage:ensure-directory pocketbase`
5. Mounting storage into pocketbase app `dokku storage:mount pocketbase /var/lib/dokku/data/storage/pocketbase:/app/pb_data`
6. Add your dokku remote `git remote add dokku dokku@ipOrHosthere:pocketbase`
7. Push to your dokku `git push dokku main`
8. Done

[Dokku docs](https://dokku.com/docs/getting-started/installation/)

## Fly.io Instructions

1. Clone this repo
2. Run `fly launch --build-only` in the root of the repo [Fly CLI instructions here](https://fly.io/docs/hands-on/install-flyctl/)
3. If you's like to reconfigure defaults - choose 'y' to be taken into the browser.
4. Run `fly volumes create pb_data --size=1`
5. In your generated fly.toml add:

```
[mounts]
  destination = "/app/pb_data"
  source = "pb_data"
```

6. Run `fly deploy --ha=false` (the `--ha` flag ensures only one machine is created, the default being 2 machines)

Your Pocketbase will be available at https://<yourapp>.fly.dev/_/

Source: [Flavio Copes](https://flaviocopes.com/run-pocketbase-on-flyio/)
