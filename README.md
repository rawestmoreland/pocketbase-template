# Pocketbase Docker Template

1. Clone this repository
2. Run `cd dokku-pocketbase`
3. Create Dokku App in your server `dokku apps:create pocketbase`
4. Create a Persistent Storage `dokku storage:ensure-directory pocketbase`
5. Mounting storage into pocketbase app `dokku storage:mount pocketbase /var/lib/dokku/data/storage/pocketbase:/app/pb_data`
6. Add your dokku remote `git remote add dokku dokku@ipOrHosthere:pocketbase`
7. Push to your dokku `git push dokku main`
8. Done
