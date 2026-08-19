# Sunshine + Moonlight — Game Streaming to the Living Room

## Why

My gaming PC lives in the bedroom, but I wanted to play its games in the living room without moving the PC or buying a second gaming rig. Sunshine + Moonlight lets me stream from the PC to the server, which is connected to the living room display — effectively turning Huginn into a thin client for the gaming PC.

It also avoids routing game streaming through Avast's VPN directly on the gaming PC — keeping that traffic on my own VPN setup instead once Tailscale is wired in (see Future Work below).

## How it's set up

This is the reverse of the "server hosts, client connects" pattern used elsewhere in this project:

- **Sunshine** runs on my primary gaming PC (bedroom) — this is the *host*, since it's the machine with the GPU and the games installed.
- **Moonlight** runs directly on the Huginn server (living room) — this is the *client*, receiving the stream and displaying it.

The plan is to also install Moonlight on my laptop later, so I can play GPU-intensive games on the go by streaming from the gaming rig, without needing powerful laptop hardware.

## Network

Currently LAN-only. Moonlight (on Huginn) connects to Sunshine (on the gaming PC) over the local network. Tailscale integration is planned but not yet wired up for this — see Future Work.

## Performance tuning

The main issue was resolution/bitrate tuning against a bandwidth-constrained network:

- My WiFi extender caps bitrate around 100 Mbps, and the initial Sunshine config was tuned too high for that ceiling — causing lag.
- Fix: reduced the graphical/stream intensity slightly and switched to **legacy mouse controls** in Moonlight.
- Result: near-lag-free streaming for both movies and games between the PC and the Ubuntu server.

## Future work

- Route the Sunshine/Moonlight connection over Tailscale instead of LAN-only, so streaming works the same way remote access does for the rest of the stack (see main README).
- Install Moonlight on my laptop to stream from the gaming PC when away from home.
