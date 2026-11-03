# Domain 11 Cheat Sheet: Simple AI Agents, APIs, and Deployment

## Basic Agent Loop
| Step | Purpose |
|---|---|
| Plan | Decide next action — call a tool or respond directly |
| Act | Execute the chosen tool/function call |
| Observe | Evaluate tool output, feed back into next Plan |

Exam note: order is always Plan → Act → Observe, repeated until a final answer is produced.

## FastAPI: Sync vs Async Endpoints
| Scenario | Use |
|---|---|
| I/O uses async library (`httpx.AsyncClient`, async DB) | `async def`, await calls |
| I/O uses blocking library (`requests`, CPU-bound inference) | plain `def` (FastAPI auto-threadpools) OR offload with `run_in_threadpool`/`asyncio.to_thread` inside `async def` |
| Blocking call inside `async def` without offload | **Anti-pattern** — blocks entire event loop, stalls all concurrent requests |

## Pydantic Request/Response Schemas
```python
from pydantic import BaseModel, Field

class PredictRequest(BaseModel):
    prompt: str = Field(..., max_length=500)
    temperature: float = Field(0.7, ge=0, le=2)
    max_tokens: int = Field(256, ge=1, le=4096)

class PredictResponse(BaseModel):
    output: str
    tokens_used: int
```
- `ge`/`le` = inclusive bounds, `gt`/`lt` = exclusive bounds
- `max_length` = string constraint
- Pydantic model as param type → auto validation + HTTP 422 on failure + auto OpenAPI docs

## Dockerizing a FastAPI AI Service
```dockerfile
FROM python:3.12-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

FROM python:3.12-slim
WORKDIR /app
COPY --from=builder /usr/local/lib/python3.12/site-packages /usr/local/lib/python3.12/site-packages
COPY . .
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

| Instruction | When it Runs |
|---|---|
| `RUN` | Build time only |
| `CMD` / `ENTRYPOINT` | Container start (exec/JSON-array form preferred — correct signal handling) |
| `EXPOSE` | Documentation only, doesn't run anything |

Best practices: slim base image, pinned `requirements.txt`, multi-stage build to drop build tools from final image.

## Deployment: Scaling & Latency
- Sync blocking calls in `async def` → serialized requests, rising tail latency
- Fix: offload to threadpool, or scale with multiple Uvicorn `--workers`
- More workers ≠ fixing event-loop blocking inside a single worker — address root cause first

## Common Exam Traps
- Confusing `RUN` (build-time) with `CMD` (runtime) for starting Uvicorn
- Using `async def` with a blocking call and no offload
- Using `min`/`max` instead of `ge`/`le` in Pydantic `Field`
- Treating TypedDict/dataclass as equivalent to Pydantic for runtime validation
