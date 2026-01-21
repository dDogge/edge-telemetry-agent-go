# Architecture

## Overview
Agent runs on Linux devices and pushes telemetry to the ingest API.

## Responsibilities
- Collect metrics (collectors)
- Optional local buffering (storage)
- Delivery with retries (sender)
- Simple health endpoint (optional)

## Data flow
1) Collect -> normalize -> enqueue
2) Dequeue -> send -> ack
3) On failure: retry with backoff