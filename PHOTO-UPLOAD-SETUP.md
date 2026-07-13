# Setting up photo uploads for the Marketplace

## 1. Create the storage bucket

1. Supabase → left sidebar → **Storage**
2. Click **New bucket**
3. Name: `listing-photos`
4. Toggle **Public bucket** to ON (so photos display on the site without extra setup)
5. Click **Create bucket**

## 2. Allow members to upload

Go to **SQL Editor → New query**, paste this, click **Run**:

```sql
create policy "authenticated users can upload listing photos"
on storage.objects for insert
to authenticated
with check (bucket_id = 'listing-photos');
```

That's it — no other setup needed. Public buckets serve images directly, so no additional read policy is required.

## 3. Upload the updated site

Same as always — upload the new `index.html` to GitHub, replacing the old one.

## What changed on the site

The "Post an item" form now has a drag-and-drop area. Members can drag an image in, or click it to pick a file the normal way, and it uploads straight to your Supabase project. The old "paste a URL" option is still there underneath, for anyone who already has a photo hosted somewhere else.
