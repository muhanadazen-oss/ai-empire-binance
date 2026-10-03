# AI EMPIRE — deployment source

This repository contains the full tested AI EMPIRE source as `ai-empire-source.tar.gz`. The archive preserves the original directory structure. See `SOURCE-MANIFEST.json` and `source.sha256` for the exact source commit and checksum.

Render verifies the checksum, extracts the code, installs locked dependencies, runs the tests, and starts the dedicated trading daemon. Use the root `render.yaml` Blueprint.

## Current status
- The web dashboard is already published separately.
- This repository does not mean a Render server has been deployed.
- Paper trading has not started. Live trading is locked.
- The two-year strategy backtest returned -5.83% net; it failed the profitability gate.
- Live trading additionally requires profitable backtest and 60 actual days of profitable paper trading, an explicit capital cap, manual owner activation, a restricted Spot-only key, a fixed individual egress IP, and tested notifications.

## Costs
The Blueprint specifies a PAID service and a PAID persistent 1 GB disk. Review and approve billing before applying. The paper deployment does not require Binance API credentials. Static egress for future live trading is a separate requirement.

## Inspect source locally
```sh
sha256sum --check source.sha256
mkdir source
tar -xzf ai-empire-source.tar.gz -C source
cd source
npm ci
npm test
```

Never commit credentials or wallet databases.
