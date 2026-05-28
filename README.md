# DigiByte Bootstrap Archive — AWM Mining

> Maintained by [AwfulWaffleMining.com](https://awfulwafflemining.com) — where all of AI goes to hash.
> Last updated: **[PENDING — sync in progress]**

---

## ⬇️ Download Bootstrap

| File | Height | Date | Size | SHA256 |
|------|--------|------|------|--------|
| [Download →](#) | TBD | TBD | ~25 GB | TBD |

*Hosted on Internet Archive (permanent, free, fast)*

---

## What's Included

- `blocks/` — raw blockchain block files
- `chainstate/` — pre-built UTXO set (critical — without this it won't bootstrap)

---

## How to Use (Linux / Server)

```bash
# 1. Stop digibyted
systemctl stop digibyted
# or: digibyte-cli stop

# 2. Backup your current data (optional)
mv ~/.digibyte/blocks ~/.digibyte/blocks.bak
mv ~/.digibyte/chainstate ~/.digibyte/chainstate.bak

# 3. Download and extract bootstrap
wget -O dgb-bootstrap.zip "ARCHIVE_URL_HERE"

# 4. Verify SHA256 checksum
sha256sum dgb-bootstrap.zip
# Should match: TBD

# 5. Extract into your DigiByte data directory
unzip dgb-bootstrap.zip -d ~/.digibyte/
# Or for a custom datadir:
# unzip dgb-bootstrap.zip -d /data/dgb/

# 6. Restart digibyted
systemctl start digibyted
# DigiByte Core will verify existing blocks (fast) and sync remaining ones
```

---

## ⚠️ Memory Warning for Small Servers

If running on a server with < 16 GB RAM, add these to `digibyte.conf` **before** starting:

```ini
dbcache=512      # safe for 8 GB servers — was 4096 by default (causes OOM!)
maxmempool=64
maxconnections=8
```

The default `dbcache` is high enough to OOM a typical VPS during IBD.

---

## Verification

DigiByte Core verifies all block headers, difficulty adjustments, merkle roots, and transactions on startup. The bootstrap only speeds up the initial download — it does not bypass any consensus checks.

---

## About

This bootstrap is created from a fully-synced DigiByte node running on the [AWM Mining](https://awfulwafflemining.com) infrastructure. AWM Mining is an AI-agent hashrate marketplace for solo DGB and BCH mining.

SHA256 verification file: `SHA256SUMS.txt`

License: MIT — free to redistribute with credit.
