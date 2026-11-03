## Chapter 11: Domain 11: Simple AI Agents, APIs, and Deployment — Practice Questions

**Q1.** A company builds a simple AI agent that answers questions using a calculator tool. The agent receives a query, decides whether to call the calculator, executes the tool if needed, then uses the result to form a final answer. Which sequence correctly describes the basic agent loop used here?

A) Observe, Act, Plan
B) Act, Observe, Plan
C) Observe, Plan, Act
D) Plan, Act, Observe

<details>
<summary>Answer</summary>

**Correct: D**

The agent first plans (decides whether/which tool to call), then acts (executes the tool), then observes (uses the result) before responding or looping again.

**Why the others are wrong:**
- Observing before acting is impossible — there is no result to observe yet.
- Acting before planning means executing a tool with no decision process, which isn't the standard loop.
- Planning must come before acting, not after observing an action that hasn't happened.

</details>

---

**Q2.** A FastAPI endpoint wraps a call to a local LLM inference function that takes 10 seconds to run and is defined as a regular synchronous Python function (not async). The endpoint itself is declared with `async def`. Under load, the API becomes unresponsive to other requests while inference runs. What is the BEST fix?

A) Increase the number of Uvicorn workers to 100
B) Add `await asyncio.sleep(0)` before calling the inference function
C) Change the Pydantic response model to use `Optional` fields
D) Convert the endpoint to use `def` instead of `async def`, or run the blocking call via `run_in_threadpool`

<details>
<summary>Answer</summary>

**Correct: D**

FastAPI automatically runs sync `def` path operations in a threadpool, or you can explicitly offload blocking code with `run_in_threadpool`/`asyncio.to_thread`, preventing the event loop from being blocked.

**Why the others are wrong:**
- Spinning up 100 workers is wasteful and doesn't fix the root cause of blocking the event loop within a single worker.
- `asyncio.sleep(0)` yields control briefly but does not offload CPU-bound/blocking work.
- Changing the response model's field types has no effect on concurrency or blocking behavior.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A team is containerizing a FastAPI-based AI inference service with Docker for production deployment. Which Dockerfile practice BEST reduces image size and attack surface while keeping the build reproducible?

A) Use the `python:latest` base image and install all dependencies with `pip install` at container runtime
B) Use `FROM scratch` and manually copy the entire Python interpreter and all system libraries
C) Use a slim base image (e.g., `python:3.12-slim`), copy a pinned `requirements.txt`, and use a multi-stage build to exclude build tools from the final image
D) Use the `ubuntu:latest` image and run `apt-get install python3` plus `pip install -r requirements.txt` without pinning versions

<details>
<summary>Answer</summary>

**Correct: C**

Slim base images plus pinned dependencies plus multi-stage builds is the standard approach for small, reproducible, secure production images.

**Why the others are wrong:**
- The `latest` tag isn't reproducible, and installing dependencies at runtime slows startup and risks version drift.
- `FROM scratch` requires manually supplying all system libraries, which is overly complex and error-prone for a Python/FastAPI service.
- Unpinned dependencies and `latest` tags break reproducibility and bloat the final image with unnecessary OS packages.

</details>

---

**Q4.** An AI service built with FastAPI needs to validate that an incoming JSON request has a `prompt` field (string, max 500 characters) and an optional `temperature` field (float between 0 and 2). Which approach is BEST suited for this requirement within FastAPI?

A) A Python `dataclasses.dataclass` with manual `if` checks in the endpoint body
B) A plain Python dictionary with `.get()` calls and no validation
C) A `TypedDict` with no runtime validation
D) A Pydantic `BaseModel` with `Field(..., max_length=500)` and `Field(0.7, ge=0, le=2)`

<details>
<summary>Answer</summary>

**Correct: D**

Pydantic models integrate natively with FastAPI to perform automatic request validation, enforce field constraints, and generate OpenAPI documentation.

**Why the others are wrong:**
- Dataclasses don't provide automatic runtime validation or standardized HTTP 422 error responses that FastAPI gives for free with Pydantic.
- A plain dict with `.get()` performs no type or constraint checking, letting invalid data through.
- TypedDict is only a static typing hint checked by tools like mypy; it enforces nothing at runtime.

</details>

---

**Q5.** A FastAPI endpoint calls an external LLM API over HTTP using an async HTTP client (`httpx.AsyncClient`) and awaits the response. Which endpoint definition is appropriate?

A) `def` endpoint, since all I/O should be synchronous
B) `async def` endpoint that calls a blocking `requests.get()` without threadpool offloading
C) `async def` endpoint that awaits the async client call
D) `def` endpoint that internally spawns a new asyncio event loop

<details>
<summary>Answer</summary>

**Correct: C**

Since the HTTP call uses an async client and is awaited, `async def` keeps the operation non-blocking within the event loop, maximizing concurrency.

**Why the others are wrong:**
- Using plain `def` forces unnecessary threadpool overhead for work that could run fully async.
- Calling a blocking `requests.get()` inside `async def` blocks the event loop for all concurrent requests — a common anti-pattern.
- Manually spawning a new event loop inside a sync function inside FastAPI/Uvicorn is unnecessary and error-prone.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** You need a Pydantic field `max_tokens` that must be an integer between 1 and 4096, defaulting to 256. Which field definition is correct?

A) `max_tokens: int = Field(256, min=1, max=4096)`
B) `max_tokens: int = Field(256, ge=1, le=4096)`
C) `max_tokens: Optional[int] = 256`
D) `max_tokens: int(256, ge=1, le=4096)`

<details>
<summary>Answer</summary>

**Correct: B**

This is valid Pydantic syntax: `Field(default, ge=, le=)` enforces inclusive lower/upper bounds with 256 as the default.

**Why the others are wrong:**
- `min`/`max` are not valid Pydantic `Field` parameters; this raises an error — the correct keywords are `ge`/`le`/`gt`/`lt`.
- `Optional[int] = 256` provides a default but enforces no range constraint at all.
- `int(256, ge=1, le=4096)` is invalid Python syntax — `int()` doesn't accept these arguments and this isn't a valid type annotation.

</details>

---

**Q7.** Which Dockerfile instruction correctly runs a FastAPI app with Uvicorn as the container's main process, binding to all interfaces on port 8000?

A) `RUN uvicorn main:app --host 0.0.0.0 --port 8000`
B) `CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]`
C) `ENTRYPOINT python main.py --serve`
D) `EXPOSE uvicorn main:app --port 8000`

<details>
<summary>Answer</summary>

**Correct: B**

CMD in exec (JSON array) form correctly starts Uvicorn as the container's foreground process and handles OS signals properly for graceful shutdown.

**Why the others are wrong:**
- RUN executes only during image build time — the server would never actually start when the container runs.
- ENTRYPOINT here is in shell form invoking a nonexistent serving mechanism (`main.py --serve`), inconsistent with the uvicorn pattern and with signal-handling issues.
- EXPOSE only documents a port for metadata purposes; it does not execute any command.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** In the basic plan-act-observe agent loop, what is the correct purpose of the 'observe' step?

A) Generate the next natural language response to the user without using any tool output
B) Select which large language model to use for the next request
C) Evaluate the result returned from the executed action/tool call to inform the next planning step
D) Validate the incoming HTTP request schema before any processing begins

<details>
<summary>Answer</summary>

**Correct: C**

'Observe' means examining the outcome of the acted-upon tool/function call, feeding that result back into the next planning iteration.

**Why the others are wrong:**
- Ignoring tool output defeats the purpose of the agent loop, which exists to incorporate real action results.
- Model selection is not part of the observe step — it occurs separately from the loop logic.
- Request schema validation is a FastAPI/Pydantic API-layer concern, unrelated to the agent's internal observe step.

</details>

---

