# Wake PC – PHP Improved Fork

Fork of [szabodanika/wake-pc](https://github.com/szabodanika/wake-pc) with enhancements for Linux PHP environments and systemd integration.

![screenshot](https://github.com/szabodanika/wake-pc/blob/master/readme-header.png)

## Features in this Fork
- **Native PHP WOL**: Replaced `netcat` (`nc`) dependency with pure PHP socket implementation for sending magic packets.
- **Improved Online Check**: Uses ICMP ping instead of `fsockopen` on arbitrary ports for better reliability.
- **Systemd-Friendly**: Fully compatible with running as a systemd service.
- **Simple Setup**: Configure `config.ini` and run with PHP's built-in server or as a systemd service.

## Quick Setup
1. Fork and clone this repository to your machine.
2. Create a directory, e.g., `/var/www/wake-pc`.
3. Copy the repository files to the directory.
4. Edit `config.ini` with your target PC(s) MAC and broadcast addresses.
5. For testing, start the PHP built-in server:
   ```bash
   php -S 0.0.0.0:9010
   ```
6. For production, create and enable a `wake-pc.service` systemd service (see original README for an example).
7. Monitor activity via systemd logs:
   ```bash
   journalctl -u wake-pc.service -f
   ```

## Differences from Original
| Feature                | Original                              | This Fork                             |
|------------------------|---------------------------------------|---------------------------------------|
| **WOL Method**         | `netcat` via `shell_exec`             | Pure PHP socket implementation        |
| **Online Check**       | `fsockopen` on configurable port      | ICMP ping                            |
| **Systemd**            | Works manually                        | Fully compatible with systemd        |

## Original Repository
[szabodanika/wake-pc](https://github.com/szabodanika/wake-pc)
