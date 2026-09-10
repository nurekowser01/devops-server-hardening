# Host Firewall Security (`devops-firewall`)

## Overview
UFW implementation with critical notes regarding Docker's interaction with `iptables`.

## The Docker Bypass Problem
Docker directly modifies `iptables` natively, which completely bypasses UFW rules. If you publish a port `0.0.0.0:5432:5432`, UFW will NOT block external access to 5432.

## The Fix
1. Bind ports to localhost: `127.0.0.1:5432:5432`.
2. Let Traefik (or a proxy) be the only container bound to `0.0.0.0:80/443`.
3. If necessary, modify the `DOCKER-USER` iptables chain.
