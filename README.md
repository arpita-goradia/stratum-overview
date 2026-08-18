# Stratum.AI

Real-time claim verification platform validating financial figures and 
academic citations against authoritative sources before they reach users.

**Live API:** https://api.stratumai.dev  
**Version:** 0.3.0 | **Status:** Production

## Architecture

User Document → Chrome Extension → FastAPI Backend → Claim Classifier
→ RAG Verifier → SEC EDGAR / Semantic Scholar / CrossRef
→ Confidence Score + Correction → User

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | FastAPI, Python, uvicorn |
| Cloud | AWS EC2, Docker, HTTPS/SSL, AWS WAF |
| AI/ML | ChromaDB, semantic embeddings, RAG pipelines |
| Security | API key auth, IP whitelisting, rate limiting, CORS |
| Data Sources | SEC EDGAR API, Semantic Scholar, CrossRef |
| Extension | Chrome Extension (Manifest V3), JavaScript |

## What It Verifies

- **Financial figures** — revenue, EPS, margins verified against SEC 10-K filings
- **Academic citations** — author, title, year verified against Semantic Scholar + CrossRef
- **Cross-domain claims** — extensible to any authoritative data source

## API Endpoints

| Endpoint | Method | Description |
|---|---|---|
| `/verify` | POST | Stratum calls LLM + verifies response |
| `/verify-text` | POST | Verify any pre-generated text |
| `/preflight` | POST | Count claims without consuming credits |
| `/usage` | GET | Usage breakdown and quota status |
| `/health` | GET/HEAD | Health check |

## Verification Results (tested Aug 2026)

| Company | Metric | Stated | SEC Filing | Verdict |
|---|---|---|---|---|
| Alphabet | FY2023 Revenue | $307.4B | $307.394B | ✅ Verified |
| Amazon | FY2023 Revenue | $574.8B | $574.785B | ✅ Verified |
| Microsoft | FY2024 Revenue | $245.1B | $245.122B | ✅ Verified |
| Apple | FY2023 Revenue | $383.3B | $383.285B | ✅ Verified |
| Tesla | FY2023 Revenue | $96.8B | $96.773B | ✅ Verified |

## Security Layers

- Layer 1: IP whitelisting per API key (live)
- Layer 2: HMAC signed requests (in progress)
- Layer 3: Mutual TLS (in progress)

## Status

- Chrome extension: built and tested
- API: live at api.stratumai.dev
- Verified claims: 500+
- Active beta users: in progress

> Core source code is proprietary. This repo documents architecture,
> API reference, and verified test results.
