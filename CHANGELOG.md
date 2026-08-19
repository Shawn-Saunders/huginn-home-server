# Changelog

All notable changes to the Huginn homelab setup are logged here, most recent first.

## 2026-08-19
- Published repo and README to GitHub as a portfolio piece.

## Earlier (pre-repo)
- Set up ZFS RAID1 (bpool/rpool) across sda/sdb.
- Deployed Docker stack: Nextcloud + MariaDB, Jellyfin, Pi-hole, Watchtower, Tailscale.
- Hardened access: SSH key-only auth, Fail2Ban, UFW, ClamAV, monthly ZFS scrub cron.
- Expanded Jellyfin storage with a dedicated 2.5" ext4 drive at `/mnt/media` (UUID-mounted).
- Built DVD ripping workflow: MakeMKV + HandBrake, H.265 MKV output, Jellyfin naming conventions.
- Fixed subtitle sync issue.
- Fixed trickplay permissions issue (root-owned files; resolved via `sudo rm -rf`; dot-prefix hidden staging folder recommended for MakeMKV).
- Resolved Nextcloud trusted domain configuration issue.
