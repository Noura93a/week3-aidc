# Capacity note (team, one page)

## The numbers

- Locked model: Qwen/Qwen2.5-1.5B-Instruct-GPTQ-Int8
- Target p95 end-to-end latency (your SLO today): 2.0 seconds
- Knee concurrency (highest concurrency whose p95 is still under target): 1
- Tokens per second at the knee: 24.07
- Max sustainable request rate at the target p95: 0.19 req/s

## The limiting family

- Memory-bound: GPU memory bandwidth limits memory transfer speeds for KV cache and model weight retrieval during the decode stage, causing $p95$ latency to climb rapidly once batch size saturates memory access pipelines.

## Why the knee, not the peak

- The knee represents the highest operational capacity that guarantees our latency SLO ($p95 \le 2.0\text{s}$), whereas the peak throughput occurs in saturation where severe queuing causes SLO failures.
